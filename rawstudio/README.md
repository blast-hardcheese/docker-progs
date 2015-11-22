Rawstudio
=========

This is a relatively straightforward Docker image that builds rawstudio from source.

USAGE
=====

    # docker build -t rawstudio .
    # docker run -it -v /media/photography:/data -e DISPLAY="$DISPLAY" -v /tmp/.X11-unix:/tmp/.X11-unix rawstudio

This assumes the user's primary UID and GID are 1000:1000. If not, feel free to override the Docker envs `UID` and `GID`.

The volume `/data` is intended as a convenient way to expose your pictures into the container.
