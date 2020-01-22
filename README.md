# Harrington Trees

Treebanked commentaries by J. Matthew Harrington and students.

## Try it Out

[https://perseids-publications.github.io/harrington-trees/](https://perseids-publications.github.io/harrington-trees/)

### Setting up automatic deployment with Travis

* `gem install travis`
* `ssh-keygen -t rsa -b 4096 -f .travis-deploy-key -N ''`
* Copy `.travis-deploy-key.pub` to clipboard
* Visit `github.com/<user>/<repository>/settings/keys`
* Click `Add deploy key`
* Title the key `Travis deploy key`, paste the contents of `.travis-deploy-key.pub`, check `Allow write access`, and click `Add key`
* `rm .travis-deploy-key.pub`
* `travis login --com`
* Open `.travis.yml` and remove the line starting with `openssl ...` in the `before_install` section
* `travis encrypt-file .travis-deploy-key --pro --add`
* Update the formatting in `.travis.yml`
* `rm .travis-deploy-key`
* `git add .travis-deploy-key.enc`
* `git commit`
* `git push`

## Installation

`yarn install`

## Running the development server

`yarn start`

## Building for deployment

Before creating a production build you need to know the path where it will be accessed.
Then run the command `PUBLIC_URL='./path/of/app' yarn build`.
This will generate a set of static files in the `build/` directory that you can serve.

For example, if you want to deploy it at `www.example.com/` then run `PUBLIC_URL='./' yarn build`.
If you want to deploy it at `www.example.com/lexica/lsj` then run
`PUBLIC_URL='./lexica/lsj' yarn build`.

## Deploying a new version to github.io

`yarn deploy`

### Updating template

* `git pull source master`
* Fix merge conflicts
* `git push origin master`

## Licenses

The code is licensed under the MIT license (see `LICENSE` file).
The treebanks are licensed under the CC0 1.0 license (see `TREEBANK_LICENSE` file).
