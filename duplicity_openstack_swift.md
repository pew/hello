# duplicity backup OpenStack Swift

```
apt-get install -y duplicity python-swiftclient python-keystoneclient
```

example for runabove.com

```
export SWIFT_USERNAME="usually-your-email-address@host.com"
export SWIFT_PASSWORD="your-super-secret-password"
export SWIFT_AUTHURL="https://auth.runabove.io/v2.0"
export SWIFT_TENANTNAME="12345678"
export SWIFT_AUTHVERSION="2"
```

```
duplicity /home swift://your.container.name
```
