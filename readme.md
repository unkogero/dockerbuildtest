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
```
#docker build ./ -t localhost/mycorretto1103 -f corretto_Dockerfile_v11_0_13
```

```
docker run -it amazoncorretto:11.0.13 bash 
yum install glibc-langpack-ja-2.26-58.amzn2.x86_64
```

```
D:\work\10_develop\50_docker\latest>docker run -it amazoncorretto:11.0.13 bash 
bash-4.2# yum install glibc-langpack-ja-2.26-58.amzn2.x86_64
Loaded plugins: ovl, priorities
AmazonCorretto                                                                                                                                                                        | 2.9 kB  00:00:00     
amzn2-core                                                                                                                                                                            | 3.7 kB  00:00:00     
(1/4): amzn2-core/2/x86_64/group_gz                                                                                                                                                   | 2.5 kB  00:00:00     
(2/4): AmazonCorretto/x86_64/primary_db                                                                                                                                               |  47 kB  00:00:00     
(3/4): amzn2-core/2/x86_64/updateinfo                                                                                                                                                 | 495 kB  00:00:00     
(4/4): amzn2-core/2/x86_64/primary_db                                                                                                                                                 |  65 MB  00:00:06     
7 packages excluded due to repository priority protections
Resolving Dependencies
--> Running transaction check
---> Package glibc-langpack-ja.x86_64 0:2.26-58.amzn2 will be installed
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-langpack-ja-2.26-58.amzn2.x86_64
--> Processing Dependency: glibc = 2.26-58.amzn2 for package: glibc-langpack-ja-2.26-58.amzn2.x86_64
--> Running transaction check
---> Package glibc.x86_64 0:2.26-56.amzn2 will be updated
--> Processing Dependency: glibc = 2.26-56.amzn2 for package: glibc-langpack-en-2.26-56.amzn2.x86_64
--> Processing Dependency: glibc = 2.26-56.amzn2 for package: glibc-minimal-langpack-2.26-56.amzn2.x86_64
--> Processing Dependency: glibc(x86-64) = 2.26-56.amzn2 for package: libcrypt-2.26-56.amzn2.x86_64
---> Package glibc.x86_64 0:2.26-58.amzn2 will be an update
---> Package glibc-common.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc-common.x86_64 0:2.26-58.amzn2 will be an update
--> Running transaction check
---> Package glibc-langpack-en.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc-langpack-en.x86_64 0:2.26-60.amzn2 will be an update
--> Processing Dependency: glibc-common = 2.26-60.amzn2 for package: glibc-langpack-en-2.26-60.amzn2.x86_64
--> Processing Dependency: glibc = 2.26-60.amzn2 for package: glibc-langpack-en-2.26-60.amzn2.x86_64
---> Package glibc-minimal-langpack.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc-minimal-langpack.x86_64 0:2.26-60.amzn2 will be an update
---> Package libcrypt.x86_64 0:2.26-56.amzn2 will be updated
---> Package libcrypt.x86_64 0:2.26-60.amzn2 will be an update
--> Running transaction check
---> Package glibc.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc.x86_64 0:2.26-58.amzn2 will be an update
--> Processing Dependency: glibc = 2.26-58.amzn2 for package: glibc-langpack-ja-2.26-58.amzn2.x86_64
---> Package glibc.x86_64 0:2.26-60.amzn2 will be an update
---> Package glibc-common.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc-common.x86_64 0:2.26-56.amzn2 will be updated
---> Package glibc-common.x86_64 0:2.26-58.amzn2 will be an update
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-langpack-ja-2.26-58.amzn2.x86_64
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-2.26-58.amzn2.i686
---> Package glibc-common.x86_64 0:2.26-60.amzn2 will be an update
--> Running transaction check
---> Package glibc.i686 0:2.26-58.amzn2 will be installed
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-2.26-58.amzn2.i686
---> Package glibc-common.x86_64 0:2.26-58.amzn2 will be an update
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-langpack-ja-2.26-58.amzn2.x86_64
--> Processing Dependency: glibc-common = 2.26-58.amzn2 for package: glibc-2.26-58.amzn2.i686
--> Finished Dependency Resolution
Error: Package: glibc-langpack-ja-2.26-58.amzn2.x86_64 (amzn2-core)
           Requires: glibc-common = 2.26-58.amzn2
           Removing: glibc-common-2.26-56.amzn2.x86_64 (installed)
               glibc-common = 2.26-56.amzn2
           Updated By: glibc-common-2.26-60.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-60.amzn2
           Available: glibc-common-2.25-10.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.25-10.amzn2.0.1
           Available: glibc-common-2.26-27.amzn2.0.4.x86_64 (amzn2-core)
               glibc-common = 2.26-27.amzn2.0.4
           Available: glibc-common-2.26-27.amzn2.0.5.x86_64 (amzn2-core)
               glibc-common = 2.26-27.amzn2.0.5
           Available: glibc-common-2.26-28.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-28.amzn2.0.1
           Available: glibc-common-2.26-30.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-30.amzn2.0.1
           Available: glibc-common-2.26-32.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-32.amzn2.0.1
           Available: glibc-common-2.26-32.amzn2.0.2.x86_64 (amzn2-core)
               glibc-common = 2.26-32.amzn2.0.2
           Available: glibc-common-2.26-34.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-34.amzn2
           Available: glibc-common-2.26-35.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-35.amzn2
           Available: glibc-common-2.26-36.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-36.amzn2
           Available: glibc-common-2.26-37.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-37.amzn2
           Available: glibc-common-2.26-38.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-38.amzn2
           Available: glibc-common-2.26-39.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-39.amzn2
           Available: glibc-common-2.26-41.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-41.amzn2
           Available: glibc-common-2.26-42.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-42.amzn2
           Available: glibc-common-2.26-43.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-43.amzn2
           Available: glibc-common-2.26-44.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-44.amzn2
           Available: glibc-common-2.26-45.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-45.amzn2
           Available: glibc-common-2.26-47.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-47.amzn2
           Available: glibc-common-2.26-48.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-48.amzn2
           Available: glibc-common-2.26-53.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-53.amzn2
           Available: glibc-common-2.26-54.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-54.amzn2
           Available: glibc-common-2.26-55.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-55.amzn2
           Available: glibc-common-2.26-57.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-57.amzn2
           Available: glibc-common-2.26-58.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-58.amzn2
           Available: glibc-common-2.26-59.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-59.amzn2
Error: Package: glibc-2.26-58.amzn2.i686 (amzn2-core)
           Requires: glibc-common = 2.26-58.amzn2
           Removing: glibc-common-2.26-56.amzn2.x86_64 (installed)
               glibc-common = 2.26-56.amzn2
           Updated By: glibc-common-2.26-60.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-60.amzn2
           Available: glibc-common-2.25-10.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.25-10.amzn2.0.1
           Available: glibc-common-2.26-27.amzn2.0.4.x86_64 (amzn2-core)
               glibc-common = 2.26-27.amzn2.0.4
           Available: glibc-common-2.26-27.amzn2.0.5.x86_64 (amzn2-core)
               glibc-common = 2.26-27.amzn2.0.5
           Available: glibc-common-2.26-28.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-28.amzn2.0.1
           Available: glibc-common-2.26-30.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-30.amzn2.0.1
           Available: glibc-common-2.26-32.amzn2.0.1.x86_64 (amzn2-core)
               glibc-common = 2.26-32.amzn2.0.1
           Available: glibc-common-2.26-32.amzn2.0.2.x86_64 (amzn2-core)
               glibc-common = 2.26-32.amzn2.0.2
           Available: glibc-common-2.26-34.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-34.amzn2
           Available: glibc-common-2.26-35.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-35.amzn2
           Available: glibc-common-2.26-36.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-36.amzn2
           Available: glibc-common-2.26-37.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-37.amzn2
           Available: glibc-common-2.26-38.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-38.amzn2
           Available: glibc-common-2.26-39.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-39.amzn2
           Available: glibc-common-2.26-41.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-41.amzn2
           Available: glibc-common-2.26-42.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-42.amzn2
           Available: glibc-common-2.26-43.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-43.amzn2
           Available: glibc-common-2.26-44.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-44.amzn2
           Available: glibc-common-2.26-45.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-45.amzn2
           Available: glibc-common-2.26-47.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-47.amzn2
           Available: glibc-common-2.26-48.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-48.amzn2
           Available: glibc-common-2.26-53.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-53.amzn2
           Available: glibc-common-2.26-54.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-54.amzn2
           Available: glibc-common-2.26-55.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-55.amzn2
           Available: glibc-common-2.26-57.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-57.amzn2
           Available: glibc-common-2.26-58.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-58.amzn2
           Available: glibc-common-2.26-59.amzn2.x86_64 (amzn2-core)
               glibc-common = 2.26-59.amzn2
 You could try using --skip-broken to work around the problem
 You could try running: rpm -Va --nofiles --nodigest
 ```