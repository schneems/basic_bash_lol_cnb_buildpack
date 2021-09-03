# Basic bash buildpack

## Package the buildpack:

```
$ pack buildpack package basic_bash --config ./package.toml --format=image
```

## Build an app:

```
# This repo is ALSO an app, see app.sh
$ pack build cutlass_image_basic_bash --path . -B heroku/buildpacks:20 --buildpack docker://basic_bash  -v
Builder heroku/buildpacks:20 is trusted
Pulling image index.docker.io/heroku/buildpacks:20
20: Pulling from heroku/buildpacks
Digest: sha256:c6b0db94eca75924969fa37bc1cbfb68cb291650abad8fea80291a758b54ad22
Status: Image is up to date for heroku/buildpacks:20
Selected run image heroku/pack:20
Pulling image heroku/pack:20
20: Pulling from heroku/pack
Digest: sha256:a4da01ddb82b6064fc9d110079ad3c7ef58e32e93999670d9a30f49e15671bae
Status: Image is up to date for heroku/pack:20
Adding buildpack samples/bash-script version 0.0.1 to builder
Setting custom order
Creating builder with the following buildpacks:
-> heroku/java@0.3.10
-> heroku/gradle@0.0.35
-> heroku/jvm@0.1.7
-> heroku/maven@0.2.5
-> heroku/procfile@0.6.2
-> heroku/scala@0.0.90
-> heroku/java-function@0.3.17
-> heroku/jvm@0.1.7
-> heroku/jvm-function-invoker@0.5.2
-> heroku/maven@0.2.5
-> heroku/ruby@0.0.1
-> heroku/procfile@0.6.2
-> heroku/python@0.3.1
-> heroku/php@0.3.1
-> heroku/go@0.3.1
-> heroku/nodejs@0.3.6
-> heroku/nodejs-engine@0.7.4
-> heroku/nodejs-npm@0.4.4
-> heroku/nodejs-typescript@0.2.3
-> heroku/nodejs-yarn@0.1.5
-> heroku/procfile@0.6.2
-> heroku/nodejs-function@0.6.0
-> heroku/nodejs-engine@0.7.4
-> heroku/nodejs-function-invoker@0.2.0
-> heroku/nodejs-npm@0.4.4
-> heroku/nodejs-typescript@0.2.3
-> samples/bash-script@0.0.1
Adding buildpack samples/bash-script@0.0.1 (diffID=sha256:dffca0aa426f02f5429ce81d61d504b15d6da971a7e4f398925ec1468810b4f5)
Using build cache volume pack-cache-library_cutlass_image_basic_bash_latest-15d1ba11246c.build
Running the creator on OS linux with:
Container Settings:
  Args: /cnb/lifecycle/creator -daemon -launch-cache /launch-cache -log-level debug -cache-dir /cache -run-image heroku/pack:20 -process-type web cutlass_image_basic_bash
  System Envs: CNB_PLATFORM_API=0.4
  Image: pack.local/builder/6b6b626e777976756c79:latest
  User: root
  Labels: map[author:pack]
Host Settings:
  Binds: pack-cache-library_cutlass_image_basic_bash_latest-15d1ba11246c.build:/cache /var/run/docker.sock:/var/run/docker.sock pack-cache-library_cutlass_image_basic_bash_latest-15d1ba11246c.launch:/launch-cache pack-layers-ndrkrydehe:/layers pack-app-jvcjxokfqz:/workspace
  Network Mode:
===> DETECTING
======== Results ========
pass: samples/bash-script@0.0.1
Resolving plan... (try #1)
samples/bash-script 0.0.1
===> ANALYZING
Previous image with name "cutlass_image_basic_bash" not found
===> RESTORING
===> BUILDING
Starting build
Running build for buildpack samples/bash-script@0.0.1
Looking up buildpack
Finding plan
Running build for buildpack Bash Script Buildpack 0.0.1
Updating buildpack plan entries
Creating plan directory
Preparing paths
Running build command
---> Bash Script buildpack

Here are the contents of the current working directory:
.:
total 24
drwxr-xr-x 3 heroku heroku 4096 Sep  1 20:19 .
drwxr-xr-x 1 root   root   4096 Sep  1 20:19 ..
-rwxr-xr-x 1 heroku heroku   41 Sep  1 20:17 app.sh
drwxr-xr-x 2 heroku heroku 4096 Sep  1 20:11 bin
-rw-r--r-- 1 heroku heroku  382 Sep  1 20:19 buildpack.toml
-rw-r--r-- 1 heroku heroku   22 Sep  1 20:13 package.toml

./bin:
total 16
drwxr-xr-x 2 heroku heroku 4096 Sep  1 20:11 .
drwxr-xr-x 3 heroku heroku 4096 Sep  1 20:19 ..
-rwxr-xr-x 1 heroku heroku  327 Sep  1 20:11 build
-rwxr-xr-x 1 heroku heroku   28 Sep  1 20:12 detect
Processing layers
Updating environment
Reading output files
Updating buildpack processes
Updating process list
Finished running build for buildpack samples/bash-script@0.0.1
Listing processes
Finished build
===> EXPORTING
no project metadata found at path 'project-metadata.toml', project metadata will not be exported
Layer 'slice-1' SHA: sha256:478843fd89ecba23dc0c05b363798146998fe21b08870cdae7e3071ea1195381
Adding 1/1 app layer(s)
Reusing tarball for layer "launcher" with SHA: sha256:888ed16fa8d433489ee42578f1277e009198b4fbe163097d10e089f589bae405
Adding layer 'launcher'
Layer 'launcher' SHA: sha256:888ed16fa8d433489ee42578f1277e009198b4fbe163097d10e089f589bae405
Reusing tarball for layer "config" with SHA: sha256:8710757e122bdeaade8a8dff9f32fe55228c92dfc3693bf3414a6034844284e3
Adding layer 'config'
Layer 'config' SHA: sha256:8710757e122bdeaade8a8dff9f32fe55228c92dfc3693bf3414a6034844284e3
Reusing tarball for layer "process-types" with SHA: sha256:83d85471d9f8a3834b4e27cf701e3f0aef220cc816d9c173c7d32cd73909a590
Adding layer 'process-types'
Layer 'process-types' SHA: sha256:83d85471d9f8a3834b4e27cf701e3f0aef220cc816d9c173c7d32cd73909a590
Adding label 'io.buildpacks.lifecycle.metadata'
Adding label 'io.buildpacks.build.metadata'
Adding label 'io.buildpacks.project.metadata'
Setting CNB_LAYERS_DIR=/layers
Setting CNB_APP_DIR=/workspace
Setting CNB_PLATFORM_API=0.4
Setting CNB_DEPRECATION_MODE=quiet
Prepending /cnb/process and /cnb/lifecycle to PATH
Setting default process type 'web'
Setting ENTRYPOINT: '/cnb/process/web'
Saving cutlass_image_basic_bash...
*** Images (5c7aa9116480):
      cutlass_image_basic_bash

*** Image ID: 5c7aa9116480261b372dc4c126d81192dac048568ba3e863aae2b11b404dd631
Successfully built image cutlass_image_basic_bash
```

## Run

```
$ docker run -it --init cutlass_image_basic_bash
lol
lol
lol
lol
```
