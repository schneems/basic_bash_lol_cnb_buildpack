# Basic bash buildpack

This basic bash CNB should create a web process that echos "lol" in a loop, it works.

## Package the buildpack:

```
pack buildpack package basic_bash --config ./package.toml --format=image
pack build cutlass_image_basic_bash --path . -B heroku/buildpacks:20 --buildpack docker://basic_bash  -v
docker run -it --init cutlass_image_basic_bash
```

Expected:

```
lol
lol
lol
lol
```

Actual:

```
lol
lol
lol
lol
```

## Debug

```
$ pack inspect cutlass_image_basic_bash | grep -B2 web
Processes:
  TYPE                 SHELL        COMMAND        ARGS
  web (default)        bash         while true; do echo 'lol'; sleep 2; done
```

