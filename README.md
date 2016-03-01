[![][image-layers-status]][img-layers]

# Build container for the Go programming language

A build container intended for running builds for the [Go][golang] programming
language **with support for bzr, git and hg**. Originally it was created for
building Go projects using the [Drone][drone] continuous integration platform
but should work in other CI environments, too.

The image is based on [Alpine Linux][alpine] version 3.3, and builds upon the
[Gliderlabs Alpine image][docker-gliderlabs].

# What is Go?

[Go][golang] (a.k.a., Golang) is a programming language first developed at
Google. It is a statically-typed language with syntax loosely derived from C,
but with additional features such as garbage collection, type safety, some
dynamic-typing capabilities, additional built-in types (e.g., variable-length
arrays and key-value maps), and a large standard library.

> [wikipedia.org/wiki/Go_(programming_language)](http://en.wikipedia.org/wiki/Go_%28programming_language%29)

![logo][golang-logo]

## Features

This container provides a plain Go 1.5/1.6 installation built from official
release packages.

Both Go containers include the following version control systems to make
`go get` happy:

* bzr
* git
* hg

## Usage

This container can be used as build image in Drone, as shown in the following
example (using a build matrix):

```yaml
build:
  image: danielsreichenbach/golang:$$GO_VERSION
  commands:
    - go get -t -v ./...
    - go build -v
    - go test -v

matrix:
  GO_VERSION:
    - 1.5
    - 1.6
```

[golang]:               https://golang.org/
[golang-logo]:          https://golang.org/doc/gopher/frontpage.png

[drone]:                https://github.com/drone/drone/

[alpine]:               https://alpinelinux.org/
[docker-gliderlabs]:    https://hub.docker.com/r/gliderlabs/alpine/

[img-layers]:           https://imagelayers.io/?images=danielsreichenbach/golang:latest "Get your own badge on imagelayers.io"
[image-layers-status]:  https://badge.imagelayers.io/danielsreichenbach/golang:latest.svg
