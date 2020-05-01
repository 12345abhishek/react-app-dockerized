# Dockerizing a React App
#### Date created: Friday May 1, 2020

I followed this tutorial: <https://mherman.org/blog/dockerizing-a-react-app/>

## Result
I am serving a live React app from a local docker container.

Complete the tutorial and run:
`$ docker container ls`

```
CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS              PORTS                  NAMES
8bf2e88f8c67        sample_sample-prod   "nginx -g 'daemon of…"   4 minutes ago       Up 4 minutes        0.0.0.0:1337->80/tcp   sample-prod
```

I have no local servers running in a terminal window, but the `docker` container I created is running behind the scenes on my computer, so I can still visit <http://localhost:1337/> and see the live app!

## Success!
