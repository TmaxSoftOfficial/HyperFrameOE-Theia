# Theia

This is a group of Theia Docker files with versions for HyperFrame Open Edition.

### Prerequisites

Docker 19.03.12 (This is a workspace's version, other versions might be compatiable with this.)

### Set up Info
1) OS : CentOS 7
2) JDK : projdk 8, build number 242
3) Theia : Theia 1.0.0^

### Directory layout                                                         

```bash                                                                             
${pwd}                                                                                             
|- plugins                                                               # plugin folder
|   |- vscode-bosh-1.15.0-RC.1.vsix                                                  
|   |- vscode-concourse-1.15.0-RC.1.vsix                                          
|   |- vscode-manifest-yaml-1.15.0-RC.1                                          
|   |- vscode-spring-boot-1.15.0-RC.1.vsix                                                     
|- cf-cli_6.47.2_linux_x86-64.tgz                                        # command line client for Cloud Foundry                       
|- nodesource.bat                                                        # Script to install the NodeSource Node.js
|- package.json                                                          # Theia config file
|- README.md                                                   
```              

### Installing

#### 1. Download a Theia Dockerfile 

#### 2. Move JDK inside unzipped Tomcat directory

```bash
$ mv <projdk-version>.tar.gz <Theia-version>_<Change_version>
```

#### 3. Build an Docker Image.

```bash
$ docker build -f ./Dockerfile --no-cache --force-rm  -t <name: ex)theia:v20.0> .
```

#### 4. Generate a Container from Image.

```bash
$ docker run -it --init -p 3000:3000 -v "/home/project" <Image name>
```

## License

This project is licensed under the Apache-2.0
