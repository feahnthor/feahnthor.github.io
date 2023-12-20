---
layout: default
title: Benny-Scraper Classes
---

# Benny-Scraper Classes

In-depth documentation of the classes within Benny-Scraper, ordered by their sequence in the application's execution.

## Table of Contents
1. [Program.cs](#program.cs)
2. [NovelProcessor](#novelprocessor)
3. [Class 2](#class-2)
   - ...other classes...

## Program.cs
The starting point of the application. Manages command-line options, database connections, and service registration.

### Properties
| Name | Type | Description |
| ---- | ---- | ----------- |
| **Logger** | `NLog.Logger` | Static logger for the class, used for logging messages throughout the application. |
| **Container** | `IContainer` | The dependency injection container that manages the lifetime of services used by the application. |
| **AreYouSure** | `string` | A constant message prompt used for confirmation dialogs within the application. |
| **Configuration** | `IConfiguration` | Holds the configuration settings loaded from `appsettings.json` or other configuration sources. |

### Methods

| Name | Parameters | Return Type | Description |
| ---- | ---------- | ----------- | ----------- |
| **Main** | `string[] args` | `void` | The entry point of the application. |
| **DeleteOldLogs** | None | `void` | Deletes logs older than 5 days. Creates log folder if not present. Logs stored in `/bennyscraper/logs`. |
| **SetupLogger** | `LogLevel logLevel` | `void` | Configures log creation and output format. Determines runtime log level (default is `LogLevel.Info`). |
| **BuildConfiguration** | None | `IConfigurationRoot` | Loads configuration from `appsettings.json` for application services. |
| **ConfigureServices** | `ContainerBuilder builder` | `void` | Registers dependencies and serializes `NovelScraperSettings` for site scraping. Sets lifetimes of dependencies. |

## NovelProcessor
_(Description and details of NovelProcessor)_

### Properties
_(Table of properties)_

### Methods
_(Table of methods)_

## Class 2
_(Continue in similar format for each class)_

... (and so on for each class)
