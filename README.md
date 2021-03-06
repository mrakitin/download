# Installing RadiaSoft Docker Containers

RadiaSoft provides Docker containers for our applications
and other open source physics codes.

## Quick Start if you already know Docker

If you already have [Docker installed](#requirements), you can run Sirepo with:

```
docker run -v $PWD:/sirepo -p 8000:8000 radiasoft/sirepo
```

If you would like to run our beamsim jupyter notebook server, do:

```
docker run -v $PWD:/home/vagrant/jupyter -p 8888:8888 radiasoft/beamsim-jupyter
```

## Install Docker

Before installing RadiaSoft containers, you'll need to install Docker:

* [Mac OS X](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/)

* [Linux](https://docs.docker.com/engine/installation/#/on-linux)

## Automatic Installer (Mac, Linux, and Cygwin)

The most straightforward way to install a RadiaSoft container image is
to create an empty directory and run the installer. For example, to
install the `sirepo` container in a new directory:

```
mkdir sirepo
cd sirepo
curl radia.run | bash
```

This will install, configure the image named by the current
directory, and run it from the current directory. The image name
is taken from the directory name.

For a complete list of containers, [see the next section](#containers).

You can also be explicit and request a different container:

```
mkdir foobar
cd foobar
curl radia.run | bash -s sirepo
```

There are a few other options (words) which may be useful, e.g.

```
curl radia.run | bash -s sirepo verbose
```

You can also be explicit about which type of image you'd like:

```
curl radia.run | bash -s sirepo vagrant
```

The order of the optional keywords after the `bash -s` do not matter.

## Startup Command

The output of the curl will also tell you how to connect to the server
and/or login to the container. It will create a command in the directory
with the same name as the container, which you can use to restart the
container. For example, to restart sirepo, just type:

```bash
$ ./radia-run

Point your browser to:

http://127.0.0.1:8000/srw

 * Running on http://0.0.0.0:8000/ (Press CTRL+C to quit)
 * Restarting with stat
```

## Development Notes

To add a downloader, just add to `installers` directory. Make
sure the name doesn't conflict with obvious words like `verbose`,
`debug`, `alpha`, `beta`, etc. The command line is just a list
of keywords that gets recognized by the installer.

You can also specify a file `radiasoft-download.sh` in any repo
directory. The installer will go to that github repo for now.

To test the installer, you can set:

```sh
install_server=~/src bash install.sh myinstaller
```

This will set the `$install_url` to `file://$HOME/src`.

You can also pass `debug` to get more output.

## Vagrant

All containers can be built as Docker images or Vagrant VirtualBox boxes. The
default is to build Docker. We highly recommend you use Docker on your
Vagrant box to run Sirepo or Beamsim-Jupyter.
