# CashBank :  Application

CashBank application is designed to manage a list of customers within a bank's portfolio. CashBank application supports deposits and withdrawals to any of the customer's bank accounts.


This application is written in .NET Core 3.1 using Visual Studio (IDE)

## Design & Solution structure

CashBank Solution currently consists of following projects (Class Libraries),


```
* CashBank.Services (All the services the application supports)

* CashBank.Services.Contracts (All the interfaces for the Services Layer)

* CashBank.Models (This consists of all the domain models which is shared across other projects)

* CashBank.UnitTests (This projects covers testing of all the services in the services project)
   
    * UnitTest Project has a TestBootstrapper class which does a one time setup and initialises services and loads test data from Data.json. 
    
```
All of the functionality is currently exposed by the Unit tests project, there is a sample Data.json within the unit tests project which loads the default bank portfolio and then forms the data source for mocking as well.

At a parent level Bank Portfolio has the bank's available balance and list of all the accounts held in the bank. Each account then has its own properties including its available balance.



## Requirements

[Install](https://dotnet.microsoft.com/download#/current) the latest .NET Core 3.x SDK

[Install](https://visualstudio.microsoft.com/vs/community/) Visual Studio 2019 Community Edition (Free)


## Packages used

This project uses the following nuget packages,

1. Autofac.Extensions.DependencyInjection
2. NUnit
3. Moq
4. NewtonSoft.Json
5. Autofac.Extras.Moq

## Running in VisualStudio

* Set Startup project: CashBank.UnitTests

* At solution level (CashBank in this case) right click and Rebuild Solution, this will restore and build all the dependencies.

* Once successfully built, from top menu click Test and then Test Explorer

* To run the tests you can right click on the Project CashBank.UnitTests and hit Run this will run all the test cases.



## Assumptions and trade-offs

Assumptions : 

* There is currenlty no UI / command line tool as they were out of scope, functionality can only be seen using tests.
* Security Layer and data layer for this project has not been implemented as security and persistence were out of scope.
* No property to state the status of bank account, assuming all bank accounts currently are open and available.
* No implementation of transactions for deposits and withdrawals as this was not part of the requirement.
* No Docker file added as there is no entry point for the application other than through tests.


Trade-Offs : 

BankAccountId is a generic string for ease of use currently for eg: "ba0001", this id will change to either a GUID or a LONG INT once persistence is implemented.
