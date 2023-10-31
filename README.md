
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

## 3. Config

An apps config are the values that are likely to change between deploys rather than the actual app itself.
This is different than a config file that doesn't change between deploys like package.json or something like that.
These values should be stored in environment variables rather than in reversion control.
Examples of these type of configuration include credentials for external services or per deploy values such as the hostname for the deploy.

## 4. Backing services

Backing services should be treated as attched resources.
A backing service is any service consumed by the app over it's lifetime.
An example might be a databse or an api accessed service like twitter etc..
A backing service typically is accessed via a url and any credentials/locations stored in the apps config.

Swapping out a local mySql database for a third party one shouldn't involve any changes to the code. Just an update to the config files.

## 5. Build, Release, Run

Each release should have a unique release id and the ability to rollback to a previous release.

## 6. Processes

Any data that needs to persist between sessions should be stored between "Stateful backing services" (a database).
Other than through the database apps should share nothing and not persist data.
Sometimes web apps will cache data on the browser and expect it to be there next time the user logs on. This is in violation of the 12 factor app because it isn't a reliable store of data.

## 7. Port Binding

Web apps should listen to a url to access a service offered by an app.
the app receives that request on that url and returns the service.

## 8. Concurrency

Each type of work should be assigned to a process type.

## 9. Disposability

Processes in the 12 factor app should be able to be started and stopped at a moments notice. Starting a process should happen quickly to provide more agility to the release process.

## 10. Dev/Prod Parity

The app should be in continuouse deployment. The developer works in an environment that is as similar as possible to production and is able to move changes to production quickly.

## 11. logs

Each process writes it's event stream to stdout. Those events can be stored in a file or watched at runtime, but the app shouldn't be acceessing and changing external files while in operation.

## 12. Admin Processes

One-off admin processes should be run in an identical environment as the regular long-running processes of the app. They run against a release, using the same codebase and config as any process run against that release. Admin code must ship with application code to avoid synchronization issues.

If you run something once than that change should be a part of the release.

# Criticism of the 12 factor app

One criticism (expressed [here](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/The-12-Factor-App-is-cloud-native-development-for-dummies)) is that the 12 steps seem to be fairly obvious and self evidant.
Is someone really going to have multiple forms of version control? and did this really need to all be spelled out?

