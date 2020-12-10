# Cisco defined steps to initialize a Router
1. Configure the device name.
```bash
Router(config)# hostname hostname
```

2. Secure privileged EXEC mode.
```bash
Router(config)# enable secret password
```

3. Secure user EXEC mode.
```bash
Router(config)# line console 0
Router(config-line)# password password
Router(config-line)# login
```

4. Secure remote Telnet / SSH access.
```bash
Router(config-line)# line vty 0 4
Router(config-line)# password password
Router(config-line)# login
Router(config-line)# transport input {ssh | telnet}
```

5. Secure all passwords in the config file.
```bash
Router(config-line)# exit
Router(config)# service password-encryption
```

6. Provide legal notification.
```bash
Router(config)# banner motd delimiter message delimiter
```

7. Save the configuration.
```bash
Router(config)# end
Router# copy running-config startup-config
```
