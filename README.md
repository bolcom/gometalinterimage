# gometalinter image
[Docker](http://www.docker.com) image for the [gometalinter](https://github.com/alecthomas/gometalinter).

The published docker image can be found at https://hub.docker.com/r/dockerbolcom/gometalinterimage/

### Usage
This bash script shows how the image can be used to lint your code. Note that this example assumes the project has [vendored](https://blog.gopheracademy.com/advent-2015/vendor-folder/) all it's dependencies (ie it doesn't need anything outside of the project directory expect the go installation).

```bash
#!/bin/bash
projectdir="/project"

docker run -ti -v "$(pwd):${projectdir}" \
               -w "${projectdir}" \
               -e "GOPATH=${projectdir}" \
               dockerbolcom/gometalinterimage:1.0 gometalinter \
                  --deadline=15s \
                  --disable=errcheck \
                  --disable=gotype \                  
                  --enable=gofmt \
                  --exclude=mock_test.go \
                  src/github.com/myaccount/myproject/...
```
