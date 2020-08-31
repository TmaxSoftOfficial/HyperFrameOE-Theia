# HyperFrameOE-Theia

This Theia docker file is for HyperFrame Open Edition.

### Prerequisites

Docker 19.03.12 (Workspace version, recommended)

### Requirements

1) OS: CentOS 7
2) JDK: ProJDK 8 (build number 242)
3) Theia: Theia 1.0.0

### Directory Structure                                                            

```bash                                                                             
${pwd}   
|- Theia-1.0.0
|   |- plugins                                                               # plugin files
|   |   |- vscode-bosh-1.15.0-RC.1.vsix                                                  
|   |   |- vscode-concourse-1.15.0-RC.1.vsix                                          
|   |   |- vscode-manifest-yaml-1.15.0-RC.1                                          
|   |   |- vscode-spring-boot-1.15.0-RC.1.vsix                                                     
|   |- cf-cli_6.47.2_linux_x86-64.tgz                                        # Command line client for Cloud Foundry                       
|   |- nodesource.bat                                                        # Script to install the NodeSource Node.js
|   |- package.json                                                          # Theia configuration file
|- README.md                                                   
```              

### Installation Steps

#### 1. Download Theia Dockerfile. 

#### 2. Build a Docker Image.

```bash
$ docker build -f ./Dockerfile --no-cache --force-rm  -t <name: ex)theia:v20.0> .
```

#### 3. Generate a Container from the Image.

```bash
$ docker run -it --init -p 3000:3000 -v "/home/project" <Image name>
```

### License 

Projects are licensed under the Apache 2.0 license.

### HyperFrameOE Service Level
[HyperFrameOE Service Level](https://github.com/TmaxSoftOfficial/HyperFrameOE-About/blob/master/ServiceLevel.md)
