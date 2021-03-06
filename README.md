# Joint

| Branch  | Build status                                                                                                 |
| ------- | ------------------------------------------------------------------------------------------------------------ |
| master  | [![Build Status](https://travis-ci.org/flapek/Joint.svg?branch=master)](https://travis-ci.org/flapek/Joint)  |
| develop | [![Build Status](https://travis-ci.org/flapek/Joint.svg?branch=develop)](https://travis-ci.org/flapek/Joint) |

## Getting started

In order to get started with Joint, simply install the core package:

```
dotnet add package Joint
```

Its sole responsibility is to expose `IJointBuilder` being used by other packages, which provides fluent API experience, similar to built-in ASP.NET Core `IServiceCollection` and `IApplicationBuilder` abstractions.

```c#
public class Program
{
    public static async Task Main(string[] args)
        => await WebHost.CreateDefaultBuilder(args)
            .ConfigureServices(services => services.AddJoint().Build())
            .Configure(app =>
            {
                //Configure the middleware
            })
            .Build()
            .RunAsync();
}
```

Whether you’re using just a Program.cs on its own (yes, you can build your web applications and microservices without a need of having Startup class and AddMvc() along with full UseMvc() middleware) or doing it with a Startup.cs included, just invoke `AddJoint()` on `IServiceCollection` instance within the `ConfigureServices()` method and start using Joint packages.

The core Joint package also registers `AppOptions` type which contains the application name (and it’s purely optional).

## Options

- name - an optional name of the application.
- service - an optional service of the application.
- instance - an optional instance of the application.
- version - an optional version of the application.
- displayBanner - display a banner (console output) with the application name during a startup, true by default.
- displayVersion - display a version (console output) with the application name during a startup, true by default.

### appsettings.json

```json
"app": {
  "name": "some service",
  "service": "some service",
  "instance": "some instance",
  "version": "1",
  "displayBanner": true,
  "displayVersion": true
}
```

![cmdRunningService][image1]

## Table of Contents

- [Joint](https://github.com/flapek/Joint)
- [Joint.Auth](https://github.com/flapek/Joint.Auth)
- [Joint.CQRS.Commands](https://github.com/flapek/Joint.CQRS.Commands)
- [Joint.CQRS.Events](https://github.com/flapek/Joint.CQRS.Events)
- [Joint.CQRS.Queries](https://github.com/flapek/Joint.CQRS.Queries)
- [Joint.DB.Mongo](https://github.com/flapek/Joint.DB.Mongo)
- [Joint.DB.Redis](https://github.com/flapek/Joint.DB.Redis)
- [Joint.Docs.Swagger](https://github.com/flapek/Joint.Docs.Swagger)
- [Joint.Exception](https://github.com/flapek/Joint.Exception)
- [Joint.Logging](https://github.com/flapek/Joint.Logging)
- [Joint.WebApi](https://github.com/flapek/Joint.WebApi)

[image1]: https://github.com/flapek/Joint-Main/blob/main/Resources/cmdRunningService.png
