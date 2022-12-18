# Docker useful Linux command line

## how to delete none images in docker?
```bash
# check none images
docker image ls | grep none | perl -alne 'print $F[2]'

# delete them
docker image rm -f $(docker image ls | grep none | perl -alne 'print $F[2]')

# list images
docker image ls
```
