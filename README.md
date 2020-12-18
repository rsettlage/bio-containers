# ARC bio-containers

This repo is for Dockerfiles for ARC Docker (ultimately Singularity) containers.  I am using tagging to control DockerHub builds.  

Each software package container is in its own subdirectory.  The git process is something like this:

For testing, just using `Dockerfile` and generic tag, for release, using `Dockerfile.release` and version tag

## Testing

(from within bio-containers/canu)
 + git add Dockerfile
 + git tag -f -a "canu" -m "testing Canu 2.1.1"
 + git commit -m "testing new canu"
 + git push -f --tags
 
In Dockerhub, for the example above, the build actions are set to:

a) Source Type: Tag
b) Source: /^canu$/  
c) Docker Tag: latest
d) Dockerfile location: Dockerfile
e) Build Context: /canu (note no trailing /)


## Release

(from within bio-containers/canu)
 + cp Dockerfile Dockerfile.2.1.1
 + cp Dockerfile.2.1.1 Dockerfile.release
 + git add Dockerfile.2.1.1
 + git add Dockerfile.release
 + git tag -f -a "canu-2.1.1" -m "releasing Canu 2.1.1"
 + git commit -m "releasing Canu 2.1.1""
 + git push -f --tags
 
In Dockerhub, for the example above, the build actions are set to:

a) Source Type: Tag
b) Source: /^canu-([0-9.]+)/  
c) Docker Tag: {\1}
d) Dockerfile location: Dockerfile.release
e) Build Context: /canu (note no trailing /)


