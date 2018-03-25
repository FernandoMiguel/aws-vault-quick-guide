# to start aws-vault login in a new temporary chrome profile:

` $ aws-vault --debug login <PROFILE> --stdout | xargs -t /Applications/Google\ Chrome\ Canary.app/Contents/MacOS/Google\ Chrome\ Canary --args --no-first-run --new-window -disk-cache-dir=$(mktemp -d /tmp/chromecanary.XXXXXX) --user-data-dir=$(mktemp -d /tmp/chromecanary.XXXXXX) `


## You can add the following alias to your bash_rc

` $ alias awslogin='aws-vault --debug login <PROFILE> --stdout | xargs -t /Applications/Google\ Chrome\ Canary.app/Contents/MacOS/Google\ Chrome\ Canary --args --no-first-run --new-window -disk-cache-dir=$(mktemp -d /tmp/chromecanary.XXXXXX) --user-data-dir=$(mktemp -d /tmp/chromecanary.XXXXXX)' `

which allows you to call Roles with:

`$ p=MY-ROLE && awslogin`


## Firefox and Chrome in private mode
Inspired by https://github.com/blimmer/zsh-aws-vault/blob/master/zsh-aws-vault.plugin.zsh

### chrome
` $ alias awslogin='aws-vault --debug login <PROFILE> --stdout | xargs -t /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --args --incognito --new-window' `

### firefox

```
function awslogin() {
  _OS=$(uname)
  _FF_LOCATION=""
  if [[ "${_OS}" == "Linux" ]]; then
    _FF_LOCATION=$(which firefox)
  fi
  if [[ "${_OS}" == "Darwin" ]]; then
    _FF_LOCATION=$(which firefox)
  fi
  aws-vault --debug login $1 --stdout | xargs -t "${_FF_LOCATION}" --private-window
}
```
