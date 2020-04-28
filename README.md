# Entity Framework Web Instructions:

First, you'll need to add a reference to the following NuGet packages within your *data* project. **MAKE SURE TO INSTALL THE SPECIFIED VERSION**

* Microsoft.EntityFrameworkCore.SqlServer - 2.1.14
* Microsoft.EntityFrameworkCore.Design - 2.1.14
* Microsoft.Extensions.Configuration.FileExtensions - 2.1.1
* Microsoft.Extensions.Configuration.Json - 2.1.1

You can then go ahead and create your `DbContext` class, however, make sure to create a constructor that takes in a connection string. See how I did it here:

https://github.com/LIT-W07GH/EFCoreWebDemo/blob/master/EFCoreWebDemo.Data/PeopleContext.cs#L7-L12

You can then create your classes that match the tables you want in your database, and then add them as a `DbSet<>` to your Context class:

https://github.com/LIT-W07GH/EFCoreWebDemo/blob/master/EFCoreWebDemo.Data/Person.cs
https://github.com/LIT-W07GH/EFCoreWebDemo/blob/master/EFCoreWebDemo.Data/PeopleContext.cs#L19

Then, you'll need to create a class that implements the interface `IDesignTimeDbContextFactory<NameOfYourDbContext>`. See mine here:

https://github.com/LIT-W07GH/EFCoreWebDemo/blob/master/EFCoreWebDemo.Data/PeopleContextFactory.cs

You'll then need to change the directory on this line to match the name of your web project:

https://github.com/LIT-W07GH/EFCoreWebDemo/blob/master/EFCoreWebDemo.Data/PeopleContextFactory.cs#L12

(at the end of that line where it says `EFCoreWebDemo.Web` by mine, change it to match the name of _your_ web project)

Once you have all that set up, you can go to the command line, you can use the nuget command line for that:

![Nuget Cmd](https://raw.githubusercontent.com/LIT-W07GH/EFCoreWebDemo/master/nuget_cmd.png)

and **make sure to go into the data projects directory**. You'll have to type something like `cd MyProject.Data` From there, you
can run both the `dotnet ef migrations add {SomeMigration}` and `dotnet ef database update` commands.

From there, you can create your repository classes as you did before, but instead of using the old style of database access code, you can now
use Entity Framework.
