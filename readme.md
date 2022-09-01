```
export DOCKER_SCAN_SUGGEST=false

# base image
docker build ./ -t localhost/mybase:1.0 -f base_Dockerfile_v1
docker tag localhost/mybase:1.0 localhost/mybase:latest

# ext from base latest
docker build ./ -t localhost/myext:1.0 -f ext_Dockerfile_v1

# result from ext ( from ext:1.0 from base:latest )
docker build ./ -t localhost/result:1.0 -f result_Dockerfile_v1

# → 1.0
docker run localhost/result:1.0 ls /base
# → 1.0
docker run localhost/result:1.0 ls /ext


# update base latest to 2.0
docker build ./ -t localhost/mybase:2.0 -f base_Dockerfile_v2
docker tag localhost/mybase:2.0 localhost/mybase:latest

# result from ext ( from ext:1.0 from base:latest )
docker build ./ -t localhost/result:1.1 -f result_Dockerfile_v1

# → 1.0
docker run localhost/result:1.1 ls /base
# → 1.0
docker run localhost/result:1.1 ls /ext


# result from ext with --no-cache  ( from ext:1.0 from base:latest )
docker build ./ -t localhost/result:1.2 -f result_Dockerfile_v1 --no-cache

# → 1.0
docker run localhost/result:1.2 ls /base
# → 1.0
docker run localhost/result:1.2 ls /ext



# ext from base latest
docker build ./ -t localhost/myext:2.0 -f ext_Dockerfile_v2

# result from ext ( from ext:2.0 from base:latest )
docker build ./ -t localhost/result:2.0 -f result_Dockerfile_v2

# → 2.0
docker run localhost/result:2.0 ls /base
# → 2.0
docker run localhost/result:2.0 ls /ext
```
