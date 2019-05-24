# About Printrun

[Printrun](https://github.com/kliment/Printrun) is a 3d printing host software.

# About

This repository only consist of Printrun Software Dockerfile. So you can use
easily the Printrun utilities inside of Docker container without downloading or
building the main repository.

## Build

```console
git clone https://github.com/utkudarilmaz/docker-printrun.git
cd docker-printrun

docker build -t printrun:latest .
```

## Usage

```console
docker run -ti --rm \
  --device /dev/ttyUSB0 \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  utkudarilmaz/printrun:latest
```

+ **--device** parameter for connecting the printer via specified device.
+ **-e DISPLAY=$DISPLAY** and **-v /tmp/.X11-unix:/tmp/.X11-unix** parameters
for using pronsole in GUI.

Of course, you can use the Pronsole utility without volume and environment
variable parameters give to container.

On default, if you run container without parameter, Pronterface will be opened.
If you want to run another Printrun utility just give that name to Docker
command's end.

Example:

```console
docker run -ti --rm \
  --device /dev/ttyUSB0 \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  utkudarilmaz/printrun:latest pronsole.py
```

**Note:** If you get *"Unable to access the X Display, is $DISPLAY set
properly?"* error you have to run below command on your console.

```console
xhost +si:localuser:root
```
