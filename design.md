you are building a simple cli abstraction of nctl, shortening some commands...

styleguide
* one ruby file
* no code comments

when developing, don't run destructive commands, please qwq

don't feature envy!!!

inspiration:
https://github.com/ninech/nctl

Api something like this:

base command: deploio-app (or find a proper shortcut)

ORG_PREFIX: renuo
ENV = branch: main
PROJECT: fizzbuzz

$ signifies placeholder

pattern:

[deploio command]
[nctl command it aliases to]

Let's go!

deploio new fizzbuzz-main $
nctl get projects | grep fizzbuzz # check if project exists
nctl create project renuo-fizzbuzz # if it does not, create it!
nctl create app main --project fizzbuzz --git-url:git@gituhb.com:renuo/fizzbuzz.git --git-revision="main" --size=mini $

deploio logs fizzbuzz-main $
nctl logs app main --project renuo-fizzbuzz $

deploio list
deploio-cli nctl get apps -A -o json | jq -r '.[] | (.metadata.namespace + "-" + .metadata.name | gsub("renuo-"; ""))'

deploio exec fizzbuzz-main $
nctl exec app main --project renuo-fizzbuzz $

deploio stats fizzbuzz-main
nctl get app main --project renuo-fizzbuzz -o stats

deploio config fizzbuzz-main
nctl get app main --project renuo-fizzbuzz -o yaml

deploio config:edit fizzbuzz-main
nctl edit app main --project renuo-fizzbuzz

deploio hosts fizzbuzz-main
nctl get app main --project renuo-fizzbuzz -o json | jq -r '.status.atProvider.hosts | map(.name) | .[]'
