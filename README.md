# aws-vault quick guide
Official tool at https://github.com/99designs/aws-vault

## Managment 
* Add aws-vault profiles
> $ aws-vault --debug add <PROFILE>

* Login to AWS Console
> $ aws-vault --debug login <PROFILE>

* Rotate aws-vault keys
> $ aws-vault --debug rotate <PROFILE>

* List aws-vault profiles, roles and sessions
> $ aws-vault --debug list

* Remove aws-vault keys
> $ aws-vault --debug remove <PROFILE>

* Clear aws-vault sessions
> $ aws-vault --debug remove --sessions-only <PROFILE>


## Usage
* aws-vault basic use with subshell
> $ aws-vault --debug exec <PROFILE> --

Starts a sub shell with the following ENV:

`AWS_DEFAULT_REGION=eu-west-1, AWS_REGION=eu-west-1, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_SESSION_TOKEN, AWS_SECURITY_TOKEN`

* aws-vault basic use with inline command
> $ aws-vault --debug exec <PROFILE> -- aws s3 ls

* Use aws-vault with custom ttl
> $ aws-vault --debug exec <PROFILE> --session-ttl=15m --assume-role-ttl=1h --

* Use aws-vault with --server backend 
> $ aws-vault --debug exec <PROFILE> --session-ttl=1h --assume-role-ttl=8h --server

A local EC2 Instance Metadata server is started. This approach has the advantage that anything that uses Amazon's SDKs will automatically refresh credentials as needed, so session times can be as short as possible. 


# aws config
[~/.aws/config example](https://github.com/FernandoMiguel/kb/blob/master/aws/config)

# chrome profile
[to start a new chrome/firefox profile per role](browsers.md)

# Linux setup
Connor wrote a guide for linux backend:
https://www.tastycidr.net/using-aws-vault-with-linux/

