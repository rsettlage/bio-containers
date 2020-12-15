# ARC bio-containers

This repo is for Dockerfiles for ARC Docker (ultimately Singularity) containers.  I am using tagging to control DockerHub builds.  

Each software package container is in its own subdirectory.  The git process is something like this:

 + git add canu/Dockerfile.2.1.1
 + git tag -f -a "canu" -m "updating Canu to 2.1.1"
 + git commit -m "pdating Canu to 2.1.1""
 + git push
 + git push -f --tags
 
In Dockerhub, the build actions are set to:

a) use tags, source = canu in the example above  
b) build context is the subdirectory, /canu/ in the above  
c) the Dockerfile extension is the version, ie 2.1.1 above  
