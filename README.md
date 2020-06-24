# Important

Issues of this repository are tracked on https://github.com/aspnetboilerplate/aspnetboilerplate. Please create your issues on https://github.com/aspnetboilerplate/aspnetboilerplate/issues.

# modular-todo-app
A sample modular todo application.

see this comment: https://github.com/aspnetboilerplate/aspnetboilerplate/issues/1476#issuecomment-277330004


What I did:

Created an AspNet Core (module zero included) application from templates (http://www.aspnetboilerplate.com/Templates)
Created a module (named TodoModule: https://github.com/aspnetboilerplate/modular-todo-app/tree/master/src/todo-module) that consists of Core (Domain), Application, EntityFramework and Web project as like any other project. It could be a single assembly, but I wanted to show layering too.

EntityFramework project has it's own independent DbContext (https://github.com/aspnetboilerplate/modular-todo-app/blob/master/src/todo-module/TodoModule.EntityFramework/EntityFramework/TodoDbContext.cs).

This module assumes that we are using Abp.Zero and there is AbpUsers table. It defines a new entity for the user (https://github.com/aspnetboilerplate/modular-todo-app/blob/master/src/todo-module/TodoModule.Core/Users/TodoUser.cs) which only contains properties those are needed for the TODO module. So, not depending on Abp.Zero and other unrelated entities.

Web project's Views folder is marked as embedded resource (https://github.com/aspnetboilerplate/modular-todo-app/blob/master/src/todo-module/TodoModule.Web/project.json#L35) as we created new embedded resource system with ABP v1.4.

Current main application has a direct dependency to TodoModule.Web, but it could be easily added as plugin. I added direct dependency just to make it simpler. Actually it does not depend on any class in the module.
