# nodejs-amazonlinux

This Dockerfile generates a docker image with Node.js and AWS CLI installed locally.

To build this image just run:

```
docker build --build-arg NODE_VERSION=8.10.0 -t nodejs-amazonlinux:8.10.0 .
```

Since we are using `nvm` to install Node.js, you can change the `NODE_VERSION` to any version that could be installed with `nvm`.
