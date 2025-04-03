# gtdAngular

## setup of dev environment

### 2025-08-12

done - git init # initialize a new git repository 

done - Copy the .devcontainer directory and all of its subfolders/subfiles. You can rename the subfolders and subfiles to whatever you like. The template I created has .NET, Angular, and NodeJS. You can make your own, but this is faster.

done - Open the root folder in VSCode. VSCode should detect the presence of devcontainer and offer to reopen the workspace inside the container.

In a terminal inside VSCode (which will also be inside the container) use the Angular CLI (ng generate) to generate a project for your UI. I like to put things in a projects folder. If you are using git and it puts it in the wrong place, you can reset the folder back to the last commit and try again.

Run that using Angular CLI (ng serve) and open it in your browser.

Create a C# webapp project also in the projects folder.

Run that using dotnet CLI (dotnet run) and open it in your browser. The URI is /weatherforecast.

### debug setup

missing package.json copy in the instructions (comment out the post install instructions in the devcontainer.json)

`npm init`
 (gtdangular, v1.0.0, desc: gtd angular app, entry point: index.js (default), test command: ng test, git repo: https://github.com/angelahe/gtdAngular.git, keywords: app gtd angular, author: Angela Henders license: ISC)

mkdir projects
cd projects
ng generate component gtdangular-ui = NOPE, angular workspace not created yet

ng new gtdangular-ui
autocomplete - yes
pseudonymous usage data - no
zoneless application without zone.js (dev preview) - N
stylesheet format - CSS
enable server side rendering an static site generation - N (default)

`cd gtdangular-ui`
`ng serve` to run ui client

`ng serve --host 0.0.0.0`

why: when listen for tcp connections, it binds to an adapter and to a port
docker assigns ip address to container
every container running has a virtual network interface card
localhost or 127.* - loopback adapter (same machine)
for security by default every physical and virtual device on network, has loopback adapter
can't access loopback adapter from elsewhere is local to the device
by convention points back to device
when listening for incoming connections, has to bind to adapters and ports
by default ng serve binds to loopback adapter at 4200
only accepts connections from the loopback adapter
browser is running on the host, vs in the container
by doing `ng serve --host 0.0.0.0`
ie binding to 0 0 0 0 is shortcut for connecting to all loopback adapters
if running a web server
devcontainer magic happens automatically
port forwarding 4200 on this mac is the same as the port inside the container
ports match but still not the adapter ng serve is listening to
webpack wasn't listening to connections from the outside world

`cd projects`
`dotnet new webapi -n GtdAngular.Api`

The template "ASP.NET Core Web API" was created successfully.

```
Processing post-creation actions...
Restoring /workspaces/gtdAngular/projects/GtdAngular.Api/GtdAngular.Api.csproj:
  Determining projects to restore...
  Restored /workspaces/gtdAngular/projects/GtdAngular.Api/GtdAngular.Api.csproj (in 2.66 sec).
Restore succeeded.
```
`cd GtdAngular.Api`
try `dotnet run`

```
Building...
warn: Microsoft.AspNetCore.Hosting.Diagnostics[15]
      Overriding HTTP_PORTS '8080' and HTTPS_PORTS ''. Binding to values defined by URLS instead 'http://localhost:5165'.
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5165
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /workspaces/gtdAngular/projects/GtdAngular.Api
warn: Microsoft.AspNetCore.HttpsPolicy.HttpsRedirectionMiddleware[3]
      Failed to determine the https port for redirect.

      === see the logs ===
2025-08-12 19:57:21.760 [info] Locating .NET runtime version 9.0.1
2025-08-12 19:57:21.817 [info] Did not find .NET 9.0.1 on path, falling back to acquire runtime via ms-dotnettools.vscode-dotnet-runtime
2025-08-12 19:57:25.618 [info] Dotnet path: /home/vscode/.vscode-server/data/User/globalStorage/ms-dotnettools.vscode-dotnet-runtime/.dotnet/9.0.8~arm64/dotnet
2025-08-12 19:57:25.618 [info] Activating C# standalone...
2025-08-12 19:57:25.734 [info] [stdout] info: Program[0]
      Server started with process ID 16988

2025-08-12 19:57:26.689 [info] [stdout] {"pipeName":"/tmp/75a9ba1e.sock"}

2025-08-12 19:57:26.689 [info] received named pipe information from server
2025-08-12 19:57:26.689 [info] client has connected to server
2025-08-12 19:57:26.727 [info] [Info  - 7:57:26 PM] [Program] Language server initialized
2025-08-12 19:57:28.469 [info] [Info  - 7:57:28 PM] [project/open] [LanguageServerProjectLoader] Successfully completed load of /workspaces/gtdAngular/projects/GtdAngular.Api/GtdAngular.Api.csproj
2025-08-12 19:57:28.469 [info] [Info  - 7:57:28 PM] [project/open] [LanguageServerProjectLoader] Completed (re)load of all projects in 00:00:01.3132114
2025-08-12 19:57:50.803 [info] Detected new installation of ms-dotnettools.csdevkit
2025-08-12 20:09:11.888 [info] [Warn  - 8:09:11 PM] [textDocument/diagnostic] [LSP] Ignoring diagnostics request for untracked document: file:///workspaces/gtdAngular/projects/GtdAngular.Api/Program.cs
2025-08-12 20:09:11.888 [info] [Warn  - 8:09:11 PM] [textDocument/diagnostic] [LSP] Ignoring diagnostics request for untracked document: file:///workspaces/gtdAngular/projects/GtdAngular.Api/Program.cs
2025-08-12 20:09:11.888 [info] [Warn  - 8:09:11 PM] [textDocument/diagnostic] [LSP] Ignoring diagnostics request for untracked document: file:///workspaces/gtdAngular/projects/GtdAngular.Api/Program.cs
2025-08-12 20:09:12.512 [info] [Error - 8:09:12 PM] [workspace/didChangeWatchedFiles] [LanguageServerProjectLoader] Error while loading /workspaces/gtdAngular/projects/GtdAngular.Api/GtdAngular.Api.csproj: Could not find file '/workspaces/gtdAngular/projects/GtdAngular.Api/GtdAngular.Api.csproj'.
2025-08-12 20:09:12.514 [info] [Info  - 8:09:12 PM] [workspace/didChangeWatchedFiles] [LanguageServerProjectLoader] Completed (re)load of all projects in 00:00:00.2279077

```

so NOPE.  try again, but refer to creating a .net project from my angular course
(delete what got created)
`cd projects`
`dotnet new webapi -controllers -n GtdAngular.Api`
`cd GtdAngular.Api`
`dotnet run`

(looks like the right files are there now ie the weather app, still getting errors on trying to run it though)
```
uilding...
warn: Microsoft.AspNetCore.Hosting.Diagnostics[15]
      Overriding HTTP_PORTS '8080' and HTTPS_PORTS ''. Binding to values defined by URLS instead 'http://localhost:5181'.
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5181
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /workspaces/gtdAngular/projects/GtdAngular.Api
warn: Microsoft.AspNetCore.HttpsPolicy.HttpsRedirectionMiddleware[3]
      Failed to determine the https port for redirect.
```

http://localhost:5181/weatherforecast

===

(install C# devkit)
(claude recommends)
configure cors for Angular frontend, since Angular app will make http requests to the api
change Program.cs

### setup of container messaging in command line

Running the postCreateCommand from devcontainer.json...

[41501 ms] Start: Run in container: /bin/sh -c sudo apt-get update && sudo apt-get install -y iputils-ping; npm install
Get:1 https://dl.yarnpkg.com/debian stable InRelease
Get:2 http://ports.ubuntu.com/ubuntu-ports noble InRelease [256 kB]
Get:3 https://dl.yarnpkg.com/debian stable/main all Packages [11.8 kB]
Get:4 https://dl.yarnpkg.com/debian stable/main arm64 Packages [11.8 kB]
Get:5 http://ports.ubuntu.com/ubuntu-ports noble-updates InRelease [126 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports noble-backports InRelease [126 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports noble-security InRelease [126 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports noble/restricted arm64 Packages [113 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports noble/multiverse arm64 Packages [274 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports noble/main arm64 Packages [1776 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports noble/universe arm64 Packages [19.0 MB]
Get:12 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 Packages [1422 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 Packages [1705 kB]
Get:14 http://ports.ubuntu.com/ubuntu-ports noble-updates/multiverse arm64 Packages [39.2 kB]
Get:15 http://ports.ubuntu.com/ubuntu-ports noble-updates/restricted arm64 Packages [2704 kB]
Get:16 http://ports.ubuntu.com/ubuntu-ports noble-backports/universe arm64 Packages [33.9 kB]
Get:17 http://ports.ubuntu.com/ubuntu-ports noble-backports/main arm64 Packages [48.8 kB]
Get:18 http://ports.ubuntu.com/ubuntu-ports noble-security/multiverse arm64 Packages [20.2 kB]
Get:19 http://ports.ubuntu.com/ubuntu-ports noble-security/universe arm64 Packages [1103 kB]
Get:20 http://ports.ubuntu.com/ubuntu-ports noble-security/main arm64 Packages [1375 kB]
Get:21 http://ports.ubuntu.com/ubuntu-ports noble-security/restricted arm64 Packages [2572 kB]
99% [Working]                                                      5466 kB/s 99% [21 Packages store 0 B]                                        5466 kB/s 100% [Working]                                                     5466 kB/s                                                                              Fetched 32.9 MB in 6s (5408 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  iputils-ping
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 44.6 kB of archives.
After this operation, 181 kB of additional disk space will be used.
Get:1 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 iputils-ping arm64 3:20240117-1ubuntu0.1 [44.6 kB]
Fetched 44.6 kB in 0s (119 kB/s)        
Selecting previously unselected package iputils-ping.
(Reading database ... 24162 files and directories currently installed.)
Preparing to unpack .../iputils-ping_3%3a20240117-1ubuntu0.1_arm64.deb ...
Unpacking iputils-ping (3:20240117-1ubuntu0.1) ...
Setting up iputils-ping (3:20240117-1ubuntu0.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
npm error code ENOENT
npm error syscall open
npm error path /workspaces/gtdAngular/package.json
npm error errno -2
npm error enoent Could not read package.json: Error: ENOENT: no such file or directory, open '/workspaces/gtdAngular/package.json'
npm error enoent This is related to npm not being able to find a file.
npm error enoent
npm error A complete log of this run can be found in: /home/vscode/.npm/_logs/2025-08-12T18_42_01_235Z-debug-0.log
[51179 ms] postCreateCommand from devcontainer.json failed with exit code 254. Skipping any further user-provided commands.
Done. Press any key to close the terminal.

## devcontainers and Rider 