# nQuake Server for Linux

### Docker

If you're interested in running nQuakesv in Docker, you can find the relevant projects here:

* [nQuakesv](https://github.com/nQuake/nquakesv) - Docker Compose project
* [nQuakesv Docker](https://github.com/niclaslindstedt/nquakesv-docker) - Docker server image
* [QTV Docker](https://github.com/niclaslindstedt/qtv-docker) - Docker QTV image
* [QWFWD Docker](https://github.com/niclaslindstedt/qwfwd-docker) - Docker QWFWD image

## Install

Run the following in a Linux shell:

```
sh <(curl -s https://raw.githubusercontent.com/nQuake/server-linux/master/src/install_nquakesv.sh)
```

For armhf (raspberry pi):

```
sh <(curl -s https://raw.githubusercontent.com/axmac/nquake-server-linux/master/src/install_nquakesv.sh)
```

You might need to install some prerequisites before running the install script:

```
apt-get install curl realpath screen unzip wget libc6-i386
```

## Running nQuakesv

```
$(cat ~/.nquakesv/install_dir)/start_servers.sh
```

## Stopping nQuakesv

```
$(cat ~/.nquakesv/install_dir)/stop_servers.sh
```

## Crontab

During installation, you can choose to install nQuakesv in your crontab.

To do this manually, add the following to your crontab (or put a file with the contents below in /etc/cron.d/):

```
echo "*/10 * * * * \$(cat ~/.nquakesv/install_dir)/start_servers.sh >/dev/null 2>&1" | sudo tee /etc/cron.d/nquakesv >/dev/null
```

## Settings

Settings are contained in `~/.nquakesv/config`.

To apply settings, you need to restart nQuakesv.

### Change number of ports

Add a new port (28508):

```
touch ~/.nquakesv/ports/28508
```

Remove a port (28508):

```
rm ~/.nquakesv/ports/28508
```

### QTV

To enable qtv (port 28000):

```
echo 28000 > ~/.nquakesv/qtv
```

To disable qtv:

```
rm ~/.nquakesv/qtv
```

### QWFWD

To enable qwfwd (port 30000):

```
echo 30000 > ~/.nquakesv/qwfwd
```

To disable qwfwd:

```
rm ~/.nquakesv/qwfwd
```

## Uninstallation

```
rm -rf $(cat ~/.nquakesv/install_dir) ~/.nquakesv
```
