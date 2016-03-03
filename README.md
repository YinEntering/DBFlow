![Image](https://github.com/agrosner/DBFlow/blob/develop/dbflow_banner.png?raw=true)

[![JitPack.io](https://img.shields.io/badge/JitPack.io-3.0.0beta4-red.svg?style=flat)](https://jitpack.io/#Raizlabs/DBFlow) [![Android Weekly](http://img.shields.io/badge/Android%20Weekly-%23129-2CB3E5.svg?style=flat)](http://androidweekly.net/issues/issue-129) [![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-DBFlow-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/1134)

A robust, powerful, and very simple ORM android database library with **annotation processing**.

The library is built on speed, performance, and approachability. It not only eliminates most boiler-plate code for dealing with databases, but also provides a powerful and simple API to manage interactions.

Let DBFlow make SQL code _flow_ like a _steady_ stream so you can focus on writing amazing apps.

# Why Use DBFlow
DBFlow was built with the intention of bringing the best of most features from other ORM database libraries and to do it even better. It was also built to not limit how you can code your problems, but make it _significantly_ easier to deal with databases on Android. Don't let an ORM or library get in your way, let the code you write in your applications be the best as possible.
- **Extensibility**: `Model` is just an interface, no subclass required, but as a convenience we recommend using `BaseModel`. You can extend non-`Model` classes in different packages and use them as your DB tables. Also you can subclass other `Model` to join the `@Column` together, and again they can be in different packages. _Also, subclass objects in this library to suit your needs_.
- **Speed**: Built with java's annotation processing code generation, there's almost zero runtime performance hit by using this library (only reflection is creation of the main, generated database module's constructor). This library saves hours of boilerplate code and maintenance by generating the code for you. With powerful model caching (multiple primary key `Model` too), you can surpass the speed of SQLite by reusing where possible. We have support for lazy-loading relationships on-demand such as `@ForeignKey` or `@OneToMany` that make queries happen super-fast.
- **SQLite Query Flow**: The queries in this library adhere as closely as possible to SQLite native queries. `select(name, screenSize).from(Android.class).where(name.is("Nexus 5x")).and(version.is(6.0)).querySingle()`
- **Open Source**: This library is fully open source and contributions are not only welcomed, but encouraged.
- **Robust**: We support `Trigger`, `ModelView`, `Index`, `Migration`, built-in database request queue to perform operations on same thread, and many more features.
- **Multiple Databases, Multiple Modules**: we seamlessly support multiple database files, database modules using DBFlow in other dependencies, simultaneously.
- **Built On SQLite**: SQLite is the most widely used database engine in world and using it as your base, you are not tied to a limited set of platforms or libraries.

# Changelog

Going forward, changes between versions exist in the [releases tab](https://github.com/Raizlabs/DBFlow/releases)

for older changes, from other xx.xx versions, check it out [here](https://github.com/Raizlabs/DBFlow/wiki)

# Usage Docs
For more detailed usage, check out these sections:

[Getting Started](usage/GettingStarted.md)

[Tables and Database Properties](usage/DBStructure.md)

[Multiple Instances of DBFlow / Database Modules](usage/DatabaseModules.md)

[SQL Statements Using the Wrapper Classes](usage/SQLQuery.md)

[Properties & Conditions](usage/Conditions.md)

[Transactions](usage/Transactions.md)

[Type Converters](usage/TypeConverters.md)

[Powerful Model Caching](usage/ModelCaching.md)

[Query Models](usage/QueryModels.md)

[Content Provider Generation](usage/ContentProviderGenerators.md)

[Migrations](usage/Migrations.md)

[Model Containers](usage/ModelContainers.md)

[Observing Models](usage/ObservableModels.md)

[Queries as Lists](usage/TableList.md)

[Triggers, Indexes, and More](usage/TriggersIndexesAndMore.md)

[SQLCipher Support](usage/SQLCipherSupport.md)

[Kotlin Extensions](usage/KotlinSupport.md)

# Including in your project
If you use KAPT (Kotlin's APT), then skip this first step.

We need to include the [apt plugin](https://bitbucket.org/hvisser/android-apt) in our classpath to enable Annotation Processing:

```groovy

buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.neenbedankt.gradle.plugins:android-apt:1.8'
    }
}

allProjects {
  repositories {
    // required to find the project's artifacts
    maven { url "https://jitpack.io" }
  }
}
```

Add the library to the project-level build.gradle, using the apt plugin to enable Annotation Processing:

```groovy

  apply plugin: 'com.neenbedankt.android-apt'

  def dbflow_version = "3.0.0-beta4"
  // or dbflow_version = "develop-SNAPSHOT" for grabbing latest dependency in your project on the develop branch
  // or 10-digit short-hash of a specific commit. (Useful for bugs fixed in develop, but not in a release yet)

  dependencies {
    apt "com.github.Raizlabs.DBFlow:dbflow-processor:${dbflow_version}"
    // kapt for kotlin apt
    compile "com.github.Raizlabs.DBFlow:dbflow-core:${dbflow_version}"
    compile "com.github.Raizlabs.DBFlow:dbflow:${dbflow_version}"

    // sql-cipher database encyrption (optional)
    compile "com.github.Raizlabs.DBFlow:dbflow-sqlcipher:${dbflow_version}"

    // kotlin extensions
    compile "com.github.Raizlabs.DBFlow:dbflow-kotlinextensions:${dbflow_version}"
  }

// if you're building with Kotlin
  kapt {
    generateStubs = true
  }
```

# Pull Requests
I welcome and encourage all pull requests. It usually will take me within 24-48 hours to respond to any issue or request. Here are some basic rules to follow to ensure timely addition of your request:
1. Match coding style (braces, spacing, etc.) This is best achieved using CMD+Option+L (Reformat code) on Mac (not sure for Windows) with Android Studio defaults.
2. If its a feature, bugfix, or anything please only change code to what you specify.
3. Please keep PR titles easy to read and descriptive of changes, this will make them easier to merge :)
4. Pull requests _must_ be made against `develop` branch. Any other branch (unless specified by the maintainers) will get rejected.
5. Have fun!

# Maintained By
[agrosner](https://github.com/agrosner) ([@agrosner](https://www.twitter.com/agrosner))
