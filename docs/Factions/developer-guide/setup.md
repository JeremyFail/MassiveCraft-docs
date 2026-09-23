![Factions3 Logo](../img/hero.png){ style="display: block; margin: 0px auto; max-height: 200px" }

# Factions3 Development Setup

## Importing Factions into your Project

In order to use the API and allow your plugin to compile, you will need to import Factions (and potentially MassiveCore) into your project. Note that you do not need to shade in the API as it will be accessible on the server when Factions is installed. Additionally, you should not need to use reflection to create instances of Factions or MassiveCore classes and access methods - if you are using reflection, you are doing something wrong! You should however be sure to safety check and not run any MassiveCore or Factions methods if the plugins themselves are not found - you can do a reflection safety check against one of the Factions3 classes or MassiveCore classes in that case.

Exact instructions on how to import the JAR into your project are beyond the scope of this development guide as it varies based on your individual development environment and your IDE. You should be able to find this information for your IDE or code editor online. Check the documentation for whatever IDE or code editor you prefer to use.

Note that the JARs provided to the public do not contain the actual source `.java` files (this decreases the size of the output JAR), so documentation of the methods will likely be missing when you import them and attempt to use them in your code. You can always build Factions yourself and in the POM files tell it to include the source code in the JAR if you wanted to have the documentation, or simply look at the documentation of the methods on GitHub. 

In the future we hope to provide Javadocs and possibly even a Javadoc JAR designed for API usage only, as well as potentially even a Maven repository. For now though, this is the current process. Check back on this page in the future as the process will hopefully change/improve with time!

## Depending on Factions

If your plugin is going to depend on Factions, you should indicate this in your `plugin.yml` to ensure Factions is loaded before your plugin. This looks something like this:

```yaml
main: com.example.yourplugin.YourPlugin
name: YourPlugin
depend: [Factions, MassiveCore]
```

If it's an optional dependency, you can use the `softdepend` field instead.

Note that you _may_ not need to actually depend on MassiveCore unless you are directly accessing API classes/methods from MassiveCore. This ultimately will depend on what you are doing with your integration and what you need out of Factions. 

While Factions itself depends on MassiveCore, technically if you are accessing MassiveCore classes/methods directly, your `plugin.yml` file should include it as a dependency. You may see console warnings if you attempt to access MassiveCore classes/methods directly without indicating it as a dependency. We recommend following best practices of the `plugin.yml` structure as you develop your integration.
