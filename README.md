# win-getaddrinfo [![Build status](https://ci.appveyor.com/api/projects/status/efdbx8ariqmchva1?svg=true)](https://ci.appveyor.com/project/StefanScherer/win-getaddrinfo)

Test code to investigate the issue [nodejs/node#2578](https://github.com/nodejs/node/issues/2578) inside a Windows Docker container.

The binary is used to test the AI_ADDRCONFIG hint flag on Windows Server 2016 TP3 as well as running inside a Windows Docker container.

See the [MSDN getaddrinfo](https://msdn.microsoft.com/en-us/library/windows/desktop/ms738520(v=vs.85).aspx#AI_ADDRCONFIG) article for more details.

## Test with AI_ADDRCONFIG hint flag

```
getaddrinfo.exe registry.npmjs.org 80 AI_ADDRCONFIG
```

## Test without AI_ADDRCONFIG hint flag

```
getaddrinfo.exe registry.npmjs.org 80 0
```

## Build exe with Windows Docker containers

Spin up a Win2016 VM and set `DOCKER_HOST` environment variable to it.
Then run

```bash
./build.sh
```

The final static release binary `getaddrinfo.exe` will be copied back to your host.
