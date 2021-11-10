# O\|D Documentation

[docs.orthogonaldevices.com](https://docs.orthogonaldevices.com)

## How to contribute

### Install the development environment

```bash
sudo apt install ruby-full build-essentials
sudo gem install bundler
bundle install
```

### Start the development web server

```bash
bundle exec jekyll serve --host 0.0.0.0 --incremental
```

Your development site will be served locally from [http://localhost:4000](http://localhost:4000).

Alternatively, if you want to be able to access the dev server from another machine:

```bash
# open the firewall to tcp connections on port 4000
sudo ufw allow 4000/tcp
# run the server
bundle exec jekyll serve --host `hostname` --incremental
# close the firewall
sudo ufw delete allow 4000/tcp
```