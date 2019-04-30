# NIXStats agent role for Trellis
Automaticly sets up the [NIXStats agent](https://github.com/NIXStats/nixstatsagent) on [Trellis](https://github.com/roots/trellis) servers

## Requirements
- [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html) 2.3 or later
- [Trellis](https://github.com/roots/trellis)
- [NIXStats](https://nixstats.com/r/60694) account (affiliate link)
- Ubuntu 16.04 (Xenial)

## Installation
Add this role to requirements.yml:
```yaml
- src: xilonz.trellis_nixstats # Case-sensitive!
  version: 0.1.0 # Check for latest version!
```
Run `$ ansible-galaxy install -r requirements.yml` to install this new role.

## Role variables

```yaml
# group_vars/<environment>/main.yml
###################################

nixstats_user_id: ''
nixstats_server_id: ''
nixstats_database_name: '' #(optional, by default first database)
nixstats_database_enabled: true #(optional)
nixstats_nginx_enabled: true #(optional)
nixstats_phpfpm_enabled: true #(optional)
```

## Hacking Trellis' Playbook

Add this role to `server.yml` **after** the last role:

```yaml
roles:
    # All other Trellis roles ...
    - { role: wordpress-setup, tags: [wordpress, wordpress-setup, letsencrypt] }
    - { role: xilonz.trellis-nixstats, tags: [nixstats]}
```

## Limitations and known issues

* Only one Database monitored per server
* NGINX Logging is not set up. 
* Doesn't detect php version to get right php-fpm folder

Pull requests are welcomed.

## See Also

* [NIXStats Github](https://github.com/NIXStats/nixstatsagent)

## Help needed
- A smarter way to get the database name of the first site, and/or a way to monitor all databases.

## Author Information

[Trellis NIXStats Agent](https://github.com/Xilonz/trellis-nixstats) is a [Steenbergen Design](https://steenbergen.design) project and maintained by Arjan Steenbergen

Special thanks to [the Roots team](https://roots.io/about/) whose [Trellis](https://github.com/roots/trellis) make this project possible.

You can help me by signing up to Nixstats using my [affiliate link](https://nixstats.com/r/60694)

## Contributing

Please see [CODE_OF_CONDUCT](./CODE_OF_CONDUCT.md) for details.

## License

[Trellis NIXStats Agent](https://github.com/Xilonz/trellis-nixstats) is released under the [MIT License](https://opensource.org/licenses/MIT).