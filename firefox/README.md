
### Running firefox inside a docker container (macOS)

Install XQuartz and restart your macOS

```
brew cask install xquartz
```

Start XQuartz and in the preferences, go to the “Security” tab and make sure you’ve got “Allow connections from network clients” ticked.

```
open -a XQuartz
```

Set the `IP` variable as the ip of your host machine. For example: 
```
IP=$(ifconfig en8 | grep inet | awk '$1=="inet" {print $2}')
```

Add the IP using Xhost 
```
xhost + $IP
```

Build the image 

```
docker build -t firefox .
```

You can now try running firefox in your container with:

```
docker run -it --rm -e DISPLAY=$IP:0 -v /tmp/.X11-unix:/tmp/.X11-unix firefox
```

