# Dockerizing a React App
#### Date created: Friday May 1, 2020

I followed this tutorial: <https://mherman.org/blog/dockerizing-a-react-app/>

## Result
I am serving a live React app from a local docker container.

Complete the tutorial and run:
`docker container ls`

```
CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS              PORTS                  NAMES
8bf2e88f8c67        sample_sample-prod   "nginx -g 'daemon of…"   4 minutes ago       Up 4 minutes        0.0.0.0:1337->80/tcp   sample-prod
```

I have no local servers running in a terminal window, but the `docker` container I created is running behind the scenes on my computer, so I can still visit <http://localhost:1337/> and see the live app!

Run `docker container stop sample-prod` to kill the container.

## What I learned about infrastructure & DevOps

I attempted to create a build toolchain from scratch this week in a scrum sprint for fun. I was able to build and deploy a [React app with yarn and parcel](https://github.com/hashbangash/dojo).

I wanted to learn about containerization and Docker is the most-loved open-source containerization software.

> Docker solves the infamous “it works on my machine” problem. Containers run the same wherever you start them!

Source: [Dockerizing Modern Web Apps](https://makeitnew.io/dockerizing-modern-web-apps-32ecdb24bc2e)

I want to wrap my dojo app inside a Docker image and run it as a container.

## About the Docker image

The Docker image I use is `node:13.12.0-alpine`.

From <https://hub.docker.com/_/node>:

#### node Docker Official Images

Node.js is a software platform for scalable server-side and networking applications. Node.js applications are written in JavaScript and can be run within the Node.js runtime on Mac OS X, Windows, and Linux without changes.

Node.js applications are designed to maximize throughput and efficiency, using non-blocking I/O and asynchronous events. Node.js applications run single-threaded, although Node.js uses multiple threads for file and network events. Node.js is commonly used for real-time applications due to its asynchronous nature.

Node.js internally uses the Google V8 JavaScript engine to execute code; a large percentage of the basic modules are written in JavaScript. Node.js contains a built-in, asynchronous I/O library for file, socket, and HTTP communication. The HTTP and socket support allows Node.js to act as a web server without additional software such as Apache.

#### node:version-alpine

This image is based on the popular Alpine Linux project, available in the alpine official image. Alpine Linux is much smaller than most distribution base images (~5MB), and thus leads to much slimmer images in general.

This variant is highly recommended when final image size being as small as possible is desired. The main caveat to note is that it does use musl libc instead of glibc and friends, so certain software might run into issues depending on the depth of their libc requirements. However, most software doesn't have an issue with this, so this variant is usually a very safe choice. See this Hacker News comment thread for more discussion of the issues that might arise and some pro/con comparisons of using Alpine-based images.

To minimize image size, it's uncommon for additional related tools (such as git or bash) to be included in Alpine-based images. Using this image as a base, add the things you need in your own Dockerfile (see the alpine image description for examples of how to install packages if you are unfamiliar).
