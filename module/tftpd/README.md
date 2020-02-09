### [![Alpine Build](https://img.shields.io/github/workflow/status/containercraft/ccio-tftpd/DockerHubBuild/alpine?label=Alpine%20Build)](https://github.com/containercraft/ccio-tftpd/actions) [![Docker Pulls](https://img.shields.io/docker/pulls/containercraft/ccio-tftpd?label=DockerHub%20Pulls)](https://hub.docker.com/r/containercraft/ccio-tftpd)    [Find on DockerHub](https://hub.docker.com/r/containercraft/ccio-tftpd) | [Repo Module](./module/tftp)

# TFTP Service: Network PXE Boot Resources    
    
### Simple container running [tftp-hpa] on [Alpine Linux]
######    Tftp will serve all all files mounted at `/tftpboot/`
```sh
sudo podman run \
             --name     ocp-tftpd                                                                     \
             --publish  172.10.0.3:69:69/tcp                                                          \
             --publish  172.10.0.3:69:69/udp                                                          \
             --volume   ~/.ccio/ocp-mini-stack/module/tftp/aux/pxelinux.cfg:/tftpboot/pxelinux.cfg:ro \
             --detach                                                                                 \
             --rm                                                                                     \
     docker.io/containercraft/ccio-tftpd:latest
```
######    Example Test Pull command
```sh
${PKG_MANAGER} install tftp-hpa
tftp ${IP} -c get "about.txt"
```
[tftp-hpa]:http://freshmeat.sourceforge.net/projects/tftp-hpa/
[Tftpd]:http://freshmeat.sourceforge.net/projects/tftp-hpa/
[Alpine Linux]:https://alpinelinux.org/