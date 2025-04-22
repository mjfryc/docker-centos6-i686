# docker-centos6-i686

Docker CentOS6-i686 images with devtoolset4, openssl-3.4.0 and cmake-3.31.0 installed.

## centos6-i686-development

Available at [Docker hub](https://hub.docker.com/r/mjfryc/centos6-i686-development).

CentOS6-i686 with _development_ software group installed.

### Run in temporary container

```bash
docker run -ti --rm --platform linux/i686 mjfryc/centos6-i686-development /bin/bash
```

### Build

```bash
docker build -t centos6-i686-development --no-cache centos6-i686-development
```

Build with plain output:
```bash
PROGRESS_NO_TRUNC=1 docker build --progress plain --platform=linux/i686 -t mjfryc/centos6-i686-development:v1 --no-cache centos6-i686-development
```

## centos6-i686-devtoolset4

Available at [Docker hub](https://hub.docker.com/r/mjfryc/centos6-i686-devtoolset4).

The  [centos6-i686-development](#centos6-i686-development) image with Devtoolset-4, CMake-3.31.0 and OpenSSL-3.4.0 installed.

> [!NOTE]
> Copy [releases / v1 / devtoolset-4-centos6-i386-0.1_oc20170208-1.2.i686.rpm](https://github.com/mjfryc/docker-centos6-i686/releases/download/v1/devtoolset-4-centos6-i386-0.1_oc20170208-1.2.i686.rpm) file to `centos6-i686-devtoolset4` dorectory before building. This file is too big to be stored in source code repository.

### Run in temporary container

```bash
docker run -ti --rm --platform linux/i686 mjfryc/centos-i686-devtoolset4 /bin/bash
```

### Build

```bash
PROGRESS_NO_TRUNC=1 docker build --progress plain --platform=linux/i686 -t mjfryc/centos6-i686-devtoolset4:v1 --no-cache centos6-i686-devtoolset4
```

The following CMake unit tests has failed:

```bash
#12 1436.0 99% tests passed, 9 tests failed out of 683
#12 1436.0 
#12 1436.0 Label Time Summary:
#12 1436.0 CUDA       =  45.71 sec*proc (15 tests)
#12 1436.0 Fortran    =  61.37 sec*proc (19 tests)
#12 1436.0 HIP        =  14.62 sec*proc (10 tests)
#12 1436.0 ISPC       =  26.69 sec*proc (7 tests)
#12 1436.0 
#12 1436.0 Total Test time (real) = 1096.16 sec
#12 1436.0 
#12 1436.0 The following tests FAILED:
#12 1436.0 	 39 - VSGNUFortran (Failed)                             Fortran
#12 1436.0 	152 - ExternalProjectUpdateSetup (Failed)
#12 1436.0 	153 - ExternalProjectUpdate (Failed)
#12 1436.0 	216 - CTest.UpdateCVS (Failed)
#12 1436.0 	270 - FortranC.Flags (Failed)                           Fortran
#12 1436.0 	372 - RunCMake.CMP0150 (Failed)
#12 1436.0 	586 - RunCMake.CommandLine (Failed)
#12 1436.0 	593 - RunCMake.ExternalProject (Failed)
#12 1436.0 	620 - RunCMake.CPack_RPM.VERSION (Failed)
```
