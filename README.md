# Heroku Toolbelt

Run the Heroku Toolbelt in a smallish (Ruby) container.

## Login

Use the image to login (`~/.netrc` must be present).

```sh
touch ~/.netrc

docker run \
  --rm \
  -it \
  -v $HOME/.netrc:/root/.netrc \
  heroku-toolbelt \
  login
```

## Usage

The image sets the entrypoint as "heroku" so you can run commands from there.

```sh
docker run \
  --rm \
  -it \
  -v $HOME/.netrc:/root/.netrc \
  technekes/heroku-toolbelt --help
```

**Bonus:** To simplify things you can create an alias. NOTE: This alias assumes your app code is at `/usr/src/app`, adjusts accordingly.

```sh
alias heroku='docker run \
  --rm \
  -it \
  -v $HOME/.netrc:/root/.netrc \
  -v $PWD:/usr/src/app \
  -w /usr/src/app \
  heroku-toolbelt'
```

Now simply reference the new alias.

```sh
> heroku --version
heroku-toolbelt/3.42.36 (x86_64-linux) ruby/2.3.0
heroku-cli/4.27.21-839acbb (amd64-linux) go1.5.3
=== Installed Plugins
heroku-apps@1.2.4
heroku-cli-addons@0.2.1
heroku-fork@4.1.1
heroku-git@2.4.5
heroku-local@4.1.7
heroku-pipelines@1.0.2
heroku-run@2.9.2
heroku-spaces@2.0.14
heroku-status@2.1.0
```
