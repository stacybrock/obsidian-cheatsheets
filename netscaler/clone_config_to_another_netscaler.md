# HOWTO Clone a Config to Another NetScaler

1. Save running config in production. See [[netscaler_cli_commands|NetScaler CLI Commands]]
2. Delete the following lines from the saved config file.

```
< set ns config -IPAddress 10.214.0.6 -netmask 255.255.255.224
< set system user nsroot roothashgoeshere -encrypted -timeout 0
< set ns hostName netscaler1
< add ns ip6 fe80::225:90ff:fe76:58c6/64 -scope link-local -type NSIP -vlan 1 -vServer DISABLED -mgmtAccess ENABLED -dynamicRouting ENABLED
< set HA node -failSafe ON
< add HA node 1 10.214.0.5
< add route 0.0.0.0 0.0.0.0 123.123.1.1
```

3. Save file as `ns.conf-staging` and copy to the target box.
4. Also copy certs from prod to target. Certs live in `/nsconfig/ssl/`
5. Run the staging conf on the target box:

```
> batch -fileName ns.conf-staging -outFile output
```

## Tags
[[netscaler]]