
# An overview of the 12 factor app design principles for building an application.

You can find more information [here](https://12factor.net/)

## What is the 12 factor app?

The 12-factor app is a methodology for building slftware-as-service apps i.e. Web-apps.

### The 12 factors are as follows.

1. Codebase
2. Dependencies
3. Config
4. Backing Services
5. Build, release, run
6. Processes
7. Port binding
8. Concurrency
9. Disposability
10. Dev/prod parity
11. Logs
12. Admin processes

## 1. Codebase

An app should contain one codebase tracked in revision control with many deploys.
There can be many running instances of an app, but their should be one main codebase.

## 2. Dependencies
All dependancies should be installed via a dependancy declaration manifest for example package.json.