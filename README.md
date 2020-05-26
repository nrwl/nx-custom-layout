# Custom Workspace Layouts

Nx can now support custom workspace layouts.

The default structure of apps and libs make sense for a lot of private projects. You often build apps supported by libs. This is not the case for oss projects, where you build libs, and use apps only for examples.

Nx 9+ supported custom layouts already. You could place your projects anywhere you wanted as long as angular.json/workspace.json point to the right place. But schematics didn't work correctly. They would assume "apps" and "libs".

Starting with Nx 9.4.0 (currently in beta), you can add the following to your nx.json:

```
  "workspaceLayout": {
    "appsDir": "packages",
    "libsDir": "packages"
  }
```

This will tell Nx where to place new apps and libs.

In the current repo all of them are created in the packages directory (try running `nx g @nrwl/angular:lib mylib`). Everything you know and love about Nx still works the same way:

- Projects can still import each other as before
- Dep graph + affected work the same way
- Caching works the same way
- ...

This workspace uses the Nx CLI and has `workspace.json`, but the exact same config can be added to an Angular CLI powered workspace.
