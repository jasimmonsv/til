# Cisco defined steps to initialize a Router
1. Configure the device name.
`Router(config)# hostname hostname`

2. Secure privileged EXEC mode.
`Router(config)# enable secret password`

3. Secure user EXEC mode.
```
Router(config)# line console 0
Router(config-line)# password password
Router(config-line)# login
```

4. Secure remote Telnet / SSH access.
```
Router(config-line)# line vty 0 4
Router(config-line)# password password
Router(config-line)# login
Router(config-line)# transport input {ssh | telnet}
```

5. Secure all passwords in the config file.
```
Router(config-line)# exit
Router(config)# service password-encryption
```

6. Provide legal notification.
`(config)# banner motd delimiter message delimiter`

7. Save the configuration.
```
Router(config)# end
Router# copy running-config startup-config
```

## SSH
```
Router# configure terminal
Router(config)# hostname R1
R1(config)# ip domain name span.com
R1(config)# crypto key generate rsa
# Setup ssh username
R1(config)# username <username> secret <password>

# Secure vty
R1(config)# line vty 0 15
R1(config-line)# login local
R1(config-line)# transport input ssh
```

## Disable unused services
```
# show ip ports all
# show control-plane host open-ports
(config)# no ip http server
(config)# line vty 0 15
(config-line)# transport input ssh
```

## Shutdown unused ports
On a switch it is a good security practice to disable unused ports. One method of doing this is to simply shut down each port with the ‘shutdown’ command. This would require accessing each port individually. There is a shortcut method for making modifications to several ports at once by using the interface range command. On SW1 all ports except FastEthernet0/1 and GigabitEthernet0/1 can be shutdown with the following command:
```
(config)# interface range F0/2-24, G0/2
(config-if-range)# shutdown

%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to administratively down
%LINK-5-CHANGED: Interface FastEthernet0/3, changed state to administratively down
<Output omitted>
%LINK-5-CHANGED: Interface FastEthernet0/24, changed state to administratively down
%LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to administratively down
```
The command used the port range of 2-24 for the FastEthernet ports and then a single port range of GigabitEthernet0/2.

## Hardening
1. Block anyone for three minutes who fails to log in after four attempts within a two-minute period.
`(config)# login block-for 180 attempts 4 within 120`
2. Set the EXEC mode timeout to 6 minutes on the VTY lines.
`(config-line)# exec-timeout 6`
