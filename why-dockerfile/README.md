# Why Dockerfile ?
- Clean image - avoid unnesssary content from image
- Create/Recreate image
- Dockerfile vs docker pull/docker load


## Dockerfile Rules:
- File must be created by 
    - Dockerfile (or)
    - dockerfile (or) 
    - anyfile (but docker build command with created file name "docker build -f filename")

- docker build <context-dir>
    - docker build .
    - docker build mydir
 
- docker build -t <tag>
- docker build -f filename

## Dockerfile Syntax:
- `#` - For comments
- `FROM base-image` - Create image from base image in docker hub
- `LABEL key=value` - Assign 
- `RUN command` - Run shell based commands or operation
- `COPY source destination` - Copy files from local system to container path
- `ADD src.tar destination` - Same like COPY but unzip/untar to destination
- `WORKDIR dir` - To set base path
- `ENTRYPOINT cmd` - Running command
- `CMD args` - Can be arguments for ENTRYPOINT

## Example:
FROM httpd:2.4
LABEL AUTHOR=user@example.com
LABEL VERSION=0.1
#COPY mypage.html /usr/local/apache2/htdocs/mypage.html (absolute path)
#WORKDIR /usr/local/apache2 (absolute path)
COPY mypage.html htdocs/mypage.html (relative path)


## Create Container For WGET:
```
FROM alpine
LABEL VERSION=0.1 \
      AUTHOR=me \
      EMAIL=me@example.com

RUN apk update \
 && apk add wget \
 && rm -rf /var/cache/apk/*

WORKDIR /root/

#ENTRYPOINT has 2syntax: shell and exec (it uses JSON array syntax)
ENTRYPOINT [ "wget" ]

#CMD has 3syntax: shell and exec and default parameters (exec/default it uses JSON array syntax)
CMD [ "--help" ]
```

- docker build -t dget .
- docker image ls
- alias dget='docker run --rm dget'
- dget example.com
- dget -> will return help console

### Bind Mounting
- docker run -v $(pwd):/root dget example.com (can be aliased by below)
- alias dget='docker run -v $(pwd):/root dget'
- dget example.com
