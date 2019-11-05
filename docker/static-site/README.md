# Package a static site into a Docker container

This exercise is in a series of parts. Use the tools you think are appropriate, and make use of documentation as you would with any day-to-day task.

1. On the console, launch a container with a web server to serve static files.

    You can use any existing image to do this -- there's no need to build one.

2. Create a `Dockerfile` to build an image containing a static copy of the files.

    This image would the "gold" one we'd release, where the container image has the static site's files baked in. Feel free to build on the same container you launched in the previous step.

3. Create a copy of the container which sources the files from the developer's workstation.

    This image should be designed for use in development environments where we'd like the files to be sourced from the host machine.
