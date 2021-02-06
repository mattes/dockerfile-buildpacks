# Rails Dockerfile Buildpack

Staged (for easier caching and tooling) Dockerfiles to bundle a Rails application. 
The final Docker image will be a [distroless](https://github.com/GoogleContainerTools/distroless) image. 

__Dockerfile.Base__ installs the base layer with apt packages. It installs Ruby and Node
via the mounted `.ruby-version` and `.node-version` files.

__Dockerfile.Build__ runs `bundle install` and `yarn install` to install dependencies.

__Dockerfile.Deploy__ builds a distroless image with just the final Rails app. 


## Usage

```
docker build -f Dockerfile.Base -t rails:base --build-arg EXTRA_PKGS='' .
docker build -f Dockerfile.Build -t rails:build .
docker build -f Dockerfile.Deploy --build-arg VERSION=123 --build-arg PURGE_PKGS='' -t rails:deploy .
```

## References 

* [My own Heroku in 30 mins - Deploy Rails apps to Google Cloud Compute Engine](https://gist.github.com/mattes/8f00da1f8ec55712e212f51a14745835)

