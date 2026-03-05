# UtilityLib

[![NuGet](https://img.shields.io/nuget/v/UtilityLib.svg)](https://www.nuget.org/packages/UtilityLib/)
[![NuGet Downloads](https://img.shields.io/nuget/dt/UtilityLib.svg)](https://www.nuget.org/packages/UtilityLib/)
[![Build](https://github.com/johnnyvz/UtilityLib/actions/workflows/build.yml/badge.svg)](https://github.com/johnnyvz/UtilityLib/actions/workflows/build.yml)
[![Publish](https://github.com/johnnyvz/UtilityLib/actions/workflows/publish-nuget.yml/badge.svg)](https://github.com/johnnyvz/UtilityLib/actions/workflows/publish-nuget.yml)

A utility library for common calculations and utilities.

## Installation

Install via NuGet Package Manager:

```bash
dotnet add package UtilityLib
```

Or via Package Manager Console:

```powershell
Install-Package UtilityLib
```


## Usage

```csharp
using UtilityLib;

// Add two numbers
int result = Calculate.Add(5, 3);
Console.WriteLine(result); // Output: 8
```


## Features

- **Calculate.Add**: Add two integers

## Requirements

- .NET 10.0 or higher

## License

This project is licensed under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
