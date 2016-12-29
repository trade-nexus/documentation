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

**1.** Clean and Build tradesharp-core

In Visual Studio with tradesharp-core, select from top menu 

```
*Build -> Batch Build -> Select All (and then uncheck TradeHub.Installer.*) -> Clean*

*Build -> Batch Build -> Build*
```

**2.** Clean and Build tradessharp-ui

In Visual Studio with tradesharp-ui, select from top menu 

```
*Build -> Batch Build -> Select All -> Clean*

*Build -> Batch Build -> Build*
```

--

**Step # 2: Creating Data Folders**

Create a folder **C:\TradeSharp**

*In TradeSharp folder*

**1.**  Create a folder **MarketDataEngine** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\MarketDataEngine\TradeHub.MarketDataEngine.Server.WindowsService\bin\Release
```

**2.**  Create a folder **OrderExecutionEngine** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\OrderExecutionEngine\TradeHub.OrderExecutionEngine.Server.WindowsService\bin\Release
```

**3.**  Create a folder **PositionEngine** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\PositionEngine\TradeHub.PositionEngine.Service\bin\Release
```

**4.**  Create a folder **TradeManager** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\TradeManager\TradeHub.TradeManager.Server.WindowsService\bin\Release
```

**5.**  Create a folder **TradeHubGui** and copy paste contents from location

```
C:\trade-nexus\tradesharp-ui\TradeHubGui\bin\Release
```

**6.**  Create a folder **Configuration** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Configuration\bin\Release
```

**7.**  Create a folder **TemplateInstaller** and copy paste contents from location

```
C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.TemplateInstaller\bin\Release
```

*At this stage you should have one C:\TradeSharp folder and seven sub-folders. If that seems to be the case, continue with next step.* 

***