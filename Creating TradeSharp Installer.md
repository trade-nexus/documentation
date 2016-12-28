## **Creating Installer for TradeSharp** ##

***

### Prerequisites  ###
1. Development Environment for TradeSharp. Follow the steps [here](https://github.com/trade-nexus/tradesharp-core#installation)
2. Frontend and Backend code for TradeSharp. Follow the steps [here](https://github.com/trade-nexus/tradesharp-core#code-cloning) to clone the code


### Assumptions ###

_It is assumed in the remianing document that the location for tradesharp-core (TradeSharp Backend) is **C:\trade-nexus\tradesharp-core** and location for tradesharp-ui (TradeSharp Frontend) is **C:\trade-nexus\tradesharp-ui**._ 

***

### Creating Installer ###

To create the TradeSharp installer, follow the steps below.

**Step # 1: Compiling Code**

* Clean and Build tradesharp-core

In Visual Studio with tradesharp-core, select from top menu 

*Build -> Batch Build -> Select All (and then uncheck TradeHub.Installer.*) -> Clean*

*Build -> Batch Build -> Build*

* Clean and Build tradessharp-ui

In Visual Studio with tradesharp-ui, select from top menu 

*Build -> Batch Build -> Select All -> Clean*

*Build -> Batch Build -> Build*

