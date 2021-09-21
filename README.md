# Daeploy Builder Images

This repository contains s2i builder images designed for Daeploy.

## Creating the image

```bash
docker build -t daeploy/s2i-python:tag ./path/to/image/dir
```

## Using the image

Use the builder image to create an application from source code or a git repo

```bash
$ s2i build test/test-app daeploy/s2i-python s2i-python-app
---> Building and installing application from source...
```

Deploy the application

```bash
$ daeploy deploy name version -i s2i-python-app
---> Building and installing application from source...
```
