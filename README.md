+ Build the dist

```bash
#!/usr/bin/env bash

if [ -f ./mian ]
then
	rm ./main
fi

rm ./main

CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o main .
```

+ Build the docker images

```Dockerfile
FROM busybox

RUN mkdir /templates
RUN mkdir /log

ADD ./config.json /config.json
ADD ./main /main
ADD ./templates /templates/

EXPOSE 8080
CMD ["/main"]
```
