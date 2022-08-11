## Lobbipad AD Sync

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

Gets users from an AD server, tranform these and send to Lobbipad mass upload API.

[Download the binary file here](https://drive.google.com/drive/folders/17BMPVRrVqRbBFxxc2RsyV0Elv9Rr6lyi?usp=sharing)

### Setup and configuration

The application looks for a configuration file named `sync-ad.yaml` at the same directory level as the binary. This file is formatted in [YAML syntax](https://en.wikipedia.org/wiki/YAML). It's possible to configure following options.

#### Required fields

* `ad_address`
* `ad_user`
* `ad_password`
* `ad_group`: this group will be synced
* `sync_api_token`: Lobbipad API token for your account

#### Optional fields

* `ad_telephone_field`

### Example config

```yaml
ad_address: ldap://10.10.1.230
ad_user: Lobbipad@Yourdomain.local
ad_password: PasswordForTheReadOnlyUser
ad_group: LobbipadUsers
ad_telephone_field: telephone
sync_api_token: 995568a45c8cbf4e6849869c6e71926ee665f7f6ec50ebed4e648d4c0fd7d5e4
```

## Test manually

If the config is present, run the packaged application and check what entries are synced to your Lobbipad account. When run, the sync application will output a `sync.log` text file with some information of every run. This will allow you to see if the sync was successful, how many entries were found etc.

## Setup a recurring sync

Ensure the script runs every x time (fe. daily). Depending on your system use a task scheduler like CRON (Linux, macOS) or Task Scheduler (Windows).

* Run x time a day using CRON/Scheduled task on host machine On Windows this is Task Scheduler.

## Advanced

### Custom Log path

It's possible to add a `--log` option when running the executable. So you can pass the path to your custom log.

```
./adsync-macos --log '~/location-to-log/test.txt'
./adsync-win --log 'c:\location-to-log\test.txt'
./adsync-linux --log '~/location-to-log/test.txt'
```
