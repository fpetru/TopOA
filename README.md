# TopOA

The Top OA C# library makes it easy to start coding with the Saxo Bank REST Open API.

Based on the [Command Query Responsibility Separation (CQRS) principle](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation), any operation is a matter of executing a command or issuing a query.

For example, in order to log on, then read a list of all positions, do this,
```csharp
            // Use the .Net Core DI container:
            IServiceProvider serviceProvider = new DefaultCompositionRoot().Initialize();

            // Log in:
            var loginCommand = new LoginCommand(Token);
            var loginCommandHandler = serviceProvider.GetService<ICommandHandler<LoginCommand>>();
            loginCommandHandler.Execute(loginCommand);

            // Get a list of positions:
            var posistionsQuery = new PositionsQuery();
            var positionsReader = serviceProvider.GetService<IQueryHandler<PositionsQuery, PositionsList>>();
            PositionsList positions = positionsReader.Query(posistionsQuery);
```

Validation and DI container setup has been omitted in the above snippet. The full examples are included in the repository.

## Deployment
The latest build (from the latest push to master on GitHub) is available on myGet.org,
 - https://www.myget.org/F/belgaard-ci/api/v3/index.json
 
Officially released builds are available on nuGet.org,
 - https://api.nuget.org/v3/index.json
 
 Note that at the time of writing this project is at version 0.1.x and there is no officially released build on nuGet.org yet.
