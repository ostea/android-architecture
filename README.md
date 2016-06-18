<<<<<<< HEAD
# Android Architecture Blueprints [beta]

[![Join the chat at https://gitter.im/googlesamples/android-architecture](https://badges.gitter.im/googlesamples/android-architecture.svg)](https://gitter.im/googlesamples/android-architecture?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

The Android framework offers a lot of flexibility when it comes to defining how
to organize and <em>architect</em> an Android app. This freedom, whilst very valuable, can also result in apps
with large classes, inconsistent naming and architectures (or lack of) that can
make testing, maintaining and extending difficult.

Android Architecture Blueprints is meant to demonstrate possible ways to help
with these common problems. In this project we offer the same application
implemented using different architectural concepts and tools.

You can use these samples as a reference or as a starting point for creating
your own apps. The focus here is on code structure, architecture, testing and
maintainability. However, bear in mind that there are many ways to build apps
with these architectures and tools, depending on your priorities, so these
shouldn't be considered canonical examples. The UI is deliberately kept simple.

## Samples

All projects are released in their own branch. Check each project's README for
more information.

### Stable samples

  * [todo-mvp/](https://github.com/googlesamples/android-architecture/tree/todo-mvp/) - Basic Model-View-Presenter architecture.
  * [todo-mvp-loaders/](https://github.com/googlesamples/android-architecture/tree/todo-mvp-loaders/) - Based on todo-mvp, fetches data using Loaders.
  * [todo-mvp-databinding/](https://github.com/googlesamples/android-architecture/tree/todo-databinding/) - Based on todo-mvp, uses the Data Binding Library.
  * [todo-mvp-clean/](https://github.com/googlesamples/android-architecture/tree/todo-mvp-clean/) - Based on todo-mvp, uses concepts from Clean Architecture.
  * [todo-mvp-dagger/](https://github.com/googlesamples/android-architecture/tree/todo-mvp-dagger/) - Based on todo-mvp, uses Dagger2 for Dependency Injection

### Samples in progress

  * [dev-todo-mvp-contentproviders/](https://github.com/googlesamples/android-architecture/tree/dev-todo-mvp-contentproviders/) - Based on todo-mvp-loaders, uses Content Providers
  * [dev-todo-mvp-rxjava/](https://github.com/googlesamples/android-architecture/tree/dev-todo-mvp-rxjava/) - Based on todo-mvp, uses RxJava for concurrency and data layer abstraction.

Also, see ["New sample" issues](https://github.com/googlesamples/android-architecture/issues?q=is%3Aissue+is%3Aopen+label%3A%22New+sample%22) for planned samples.

### Unofficial samples
These are community contributions that may not be in sync with the rest of the branches.
 * [todo-mvp-fragmentless/](https://github.com/Syhids/android-architecture/tree/todo-mvp-fragmentless) - Based on todo-mvp, uses Android views instead of Fragments.

### What does <em>beta</em> mean?

We're still making decisions that could affect all samples so we're keeping the
initial number of variants low before the stable release.

## Why a to-do application?

The aim of the app is to be simple enough that it's understood quickly, but
complex enough to showcase difficult design decisions and testing scenarios.
Check out the [app's specification](https://github.com/googlesamples/android-architecture/wiki/To-do-app-specification).

<img src="https://github.com/googlesamples/android-architecture/wiki/images/tasks2.png" alt="Screenshot" width="160" style="display: inline; float: right"/>

Also, a similar project exists to compare JavaScript frameworks, called [TodoMVC](https://github.com/tastejs/todomvc).

## Which sample should I choose for my app?

That's for you to decide: each sample has a README where you'll find metrics
and subjective assessments. Your mileage may vary depending on the size of the
app, the size and experience of your team, the amount of maintenance that you
foresee, whether you need a tablet layout or support multiple platforms, how
compact you like your codebase, etc.

## Opening a sample in Android Studio

First check out one of the sample branches (`master` won't compile), and then choose to open the `todoapp/` directory. Example:

  * `git clone git@github.com:googlesamples/android-architecture.git`
  * `git checkout todo-mvp` (or replace `todo-mvp` with the project you want to check out)
  * In Android Studio open the `todoapp/` directory.

## Who is behind this project?

This project is **built by the community** and curated by Google and core maintainers.

### External contributors

[David González](http://github.com/malmstein) - Core developer (Content Providers sample)

[Karumi](http://github.com/Karumi) - Developers (MVP Clean architecture sample)

[Erik Hellman](https://github.com/ErikHellman) - Developer (MVP RxJava sample)

[Saúl Molinero](https://github.com/saulmm) - Developer (MVP Dagger sample)

### Googlers

[Jose Alcérreca](http://github.com/JoseAlcerreca) - Lead/Core developer

[Natalie Masse](http://github.com/freewheelnat) - Core developer

[Stephan Linzner](http://github.com/slinzner) - Core developer

[Mustafa Kurtuldu](https://github.com/mustafa-x) - UX/design

Want to be part of it? Read [how to become a contributor](https://github.com/googlesamples/android-architecture/blob/master/CONTRIBUTING.md) and the [contributor's guide](https://github.com/googlesamples/android-architecture/wiki/Contributions)
=======
# TODO-MVP

### Summary

This sample is the base for many of the variants. It showcases a simple
implementation of the Model-View-Presenter pattern with no architectural
frameworks. It uses manual dependency injection to provide a repository with
local and remote data sources. Asynchronous tasks are handled with callbacks.

<img src="https://github.com/googlesamples/android-architecture/wiki/images/mvp.png" alt="Diagram"/>

Note: in a MVP context, the term "view" is overloaded:

  * The class android.view.View will be referred to as "Android View"
  * The view that receives commands from a presenter in MVP, will be simply called
"view".

### Fragments

It uses fragments for two reasons:

  * The separation between Activity and Fragment fits nicely with this
implementation of MVP: the Activity is the overall controller that creates and
connects views and presenters.
  * Tablet layout or screens with multiple views take advantage of the Fragments
framework.

### Key concepts

There are four features in the app:

  * <code>Tasks</code>
  * <code>TaskDetail</code>
  * <code>AddEditTask</code>
  * <code>Statistics</code>

Each feature has:

  * A contract defining the view and the presenter
  * An Activity which is responsible for the creation of fragments and presenters
  * A Fragment which implements the view interface. 
  * A presenter which implements the presenter interface

In general, the business logic lives in the presenter and relies on the view to
do the Android UI work. 

The view contains almost no logic: it converts the presenter's commands to UI
actions and listens to user actions, which are passed to the presenter. 

Contracts are interfaces used to define the connection between views and
presenters.

### Dependencies

  * Common Android support libraries (<code>com.android.support.\*)</code>
  * Android Testing Support Library (Espresso, AndroidJUnitRunner…)
  * Mockito
  * Guava (null checking)

## Features

### Complexity - understandability

#### Use of architectural frameworks/libraries/tools: 

None 

#### Conceptual complexity 

Low, as it's a pure MVP implementation for Android

### Testability

#### Unit testing

High, presenters are unit tested as well as repositories and data sources.

#### UI testing

High, injection of fake modules allow for testing with fake data

### Code metrics

Compared to a traditional project with no architecture in place, this sample
introduces additional classes and interfaces: presenters, a repository,
contracts, etc. So lines of code and number of classes are higher in MVP.


```
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Java                            46           1075           1451           3451
XML                             34             97            337            601
-------------------------------------------------------------------------------
SUM:                            80           1172           1788           4052
-------------------------------------------------------------------------------
```
### Maintainability

#### Ease of amending or adding a feature

High. 

#### Learning cost

Low. Features are easy to find and the responsibilities are clear. Developers
don't need to be familiar with any external dependency to work on the project.
>>>>>>> 789eb1fe00c28bd26f286af9842b4b159e1d6d3e

