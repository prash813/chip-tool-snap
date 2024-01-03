## Purpose 
This is an attempt to snap out matter chip-tool application, which is a reference implementation of matter controller node application.

## How to build
- Install ubuntu 22.04 lxc container in your host dev environment.
- Install snapcraft 7.x in the container.
- Ensure that you will have build-essentials installed in this container.
- Clone this repo.
- To build the snap use following command at bash prompt inside your container

``` 
  	snapcraft --destructive-mode 
			OR for arm64 and amd64 build machine
  	snapcraft --destructive-mode --verbosity=verbose --build-for=arm64

```
  

## Notes

- One of the major thing that is added in this chip-tool snap version is support for production grade matter-devices devices .

- Since matter source code is very big, downloading whole source can take considerable amount of time, which affects snap build time. So local build is enabled , for this first time you have to build the snap without defining any environment varible
 then for successive builds ensure that you move ```parts/matter-dev/build to $SNAPCRAFT_PROJECT_DIR/```
 and export LOCAL_BUILD="YES" in the build environment, then build the snap.

- for building for arm64 you need install c/c++ compiler for arm and other build tools.

- To test this snap
   - Install the snap
     - ``` snap install chip-tool_0.1_amd64.snap --dangerous```
     - ``` snap connect chip-tool:bluez ```
  - May be you can try simple pairing operation over ethernet by using following command line once the snap is installed,
    - ``` chip-tool pairing ethernet 1 20202021 3840 <ip of device node> 5543 ```
    
   The above command will start matter controller node for server device node you can build and run  linux placeholder device app from matter repo.

- Finally check out the matter repo for more details. Starting point  can be following      
  [matter-build-guide](https://github.com/project-chip/connectedhomeip/blob/master/docs/guides/BUILDING.md)
