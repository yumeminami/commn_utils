## Systemd

### Reload all services

```bash
sudo systemctl daemon-reload
```

### Enable service on boot

```bash
sudo systemctl enable <service_name>
```

### Disable service on boot

```bash
sudo systemctl disable <service_name>
```

### Reload service after modify

```bash
sudo systemctl reload <service_name>
```

### Start service

```bash
sudo systemctl start <service_name>
```

### Stop service

```bash
sudo systemctl stop <service_name>
```

### Restart service

```bash
sudo systemctl restart <service_name>
```

### Check service status

```bash
sudo systemctl status <service_name>
```

### Check service logs

```bash
sudo journalctl -u <service_name>
```

### Check service logs with follow

```bash
sudo journalctl -u <service_name> -f
```

### Check service logs with follow and lines

```bash
sudo journalctl -u <service_name> -f -n 100
```


### Configure service

* The configure file is located at `/etc/systemd/system/<service_name>.service`

* The configure file includes the following sections:

  * `[Unit]`: The dependencies and ordering of the service.

  * `[Service]`: The service itself.

  * `[Install]`: How to install the service.

* `[Uint]` Module

  * `Description`: The description of the service.

  * `After`: The service will start after the specified services.

  * `Before`: The service will start before the specified services.

  * `Requires`: The service requires the specified services.

  * `Wants`: The service wants the specified services.

* `[Service]` Module

  * `Type`: The type of the service.(`simple`, `forking`, `oneshot`, `dbus`, `notify`, `idle`)

  * `ExecStart`: The command to start the service.

  * `ExecStop`: The command to stop the service.

  * `Restart`: The service will restart after the specified seconds.

  * `RestartSec`: The seconds to restart the service.

  * `User`: The user to run the service.

  * `Group`: The group to run the service.

  * `WorkingDirectory`: The working directory of the service.

  * `Environment`: The environment variables of the service.

  * `StandardOutput`: The standard output of the service.

  * `StandardError`: The standard error of the service.

  * `SyslogIdentifier`: The syslog identifier of the service.

  * `SyslogFacility`: The syslog facility of the service.

  * `SyslogLevel`: The syslog level

* `[Install]` Module

  * `WantedBy`: The target to install the service.

  * `RequiredBy`: The target to require the service.

  * `Alias`: The alias of the service.

### Example

```bash
$ systemctl cat sshd.service

[Unit]
Description=OpenSSH server daemon
Documentation=man:sshd(8) man:sshd_config(5)
After=network.target sshd-keygen.service
Wants=sshd-keygen.service

[Service]
EnvironmentFile=/etc/sysconfig/sshd
ExecStart=/usr/sbin/sshd -D $OPTIONS
ExecReload=/bin/kill -HUP $MAINPID
Type=simple
KillMode=process
Restart=on-failure
RestartSec=42s

[Install]
WantedBy=multi-user.target
Alias=sshd.service
```

* Notice:
  * All paths in the configure file are absolute paths.
  * If the program invloves any file path, the path should be absolute path. For example, a config path is `~/.config`, it should be `/home/<user>/.config`, but if the user is root, the program can not find the correct path.
  