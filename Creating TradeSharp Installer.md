## **Creating Installer for TradeSharp** ##

***

### Prerequisites ###
1. Development Environment for TradeSharp. Follow the steps [here](https://github.com/trade-nexus/tradesharp-core#installation)
2. Frontend and Backend code for TradeSharp. Follow the steps [here](https://github.com/trade-nexus/tradesharp-core#code-cloning) to clone the code


### Assumptions ###

_It is assumed in the remaining document that the location for tradesharp-core (TradeSharp Backend) is **C:\trade-nexus\tradesharp-core** and location for tradesharp-ui (TradeSharp Frontend) is **C:\trade-nexus\tradesharp-ui**._ 

***

### Creating Installer ###

To create the TradeSharp installer, follow the steps below.

**Step # 1: Compiling Code**

**1.** Clean and Build tradesharp-core

In Visual Studio with tradesharp-core, select from top menu 

```
Build -> Batch Build -> Select All (and then uncheck TradeHub.Installer.*) -> Clean

Build -> Batch Build -> Build
```

**2.** Clean and Build tradessharp-ui

In Visual Studio with tradesharp-ui, select from top menu 

```
Build -> Batch Build -> Select All -> Clean

Build -> Batch Build -> Build
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

--

**Step # 3: Updating and Running Batch (.bat) File**

Open "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.LaunchConditions\TradeHub-Automated-Installer.bat" in notepad++

The file should contain the following content.

```
heat dir "C:\TradeSharp\MarketDataEngine" -dr TradeHub.MDE -cg TradeHub.MDE -gg -g1 -sf -srd -sreg -var "var.MyDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\MDE.wxs"

heat dir "C:\TradeSharp\OrderExecutionEngine" -dr TradeHub.OEE -cg TradeHub.OEE -gg -g1 -sf -srd -sreg -var "var.OEEDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\OEE.wxs"

heat dir "C:\TradeSharp\PositionEngine" -dr TradeHub.PE -cg TradeHub.PE -gg -g1 -sf -srd -sreg -var "var.PEDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\PE.wxs"

heat dir "C:\TradeSharp\TradeManager" -dr TradeHub.TM -cg TradeHub.TM -gg -g1 -sf -srd -sreg -var "var.TMDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\TM.wxs"

heat dir "C:\TradeSharp\TradeHubGui" -dr TradeHub.UI -cg TradeHub.UI -gg -g1 -sf -srd -sreg -var "var.UIDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\UI.wxs"

heat dir "C:\TradeSharp\Configuration" -dr TradeHub.IS -cg TradeHub.IS -gg -g1 -sf -srd -sreg -var "var.ISDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\IS.wxs"

heat dir "C:\TradeSharp\TemplateInstaller" -dr TradeHub.TS -cg TradeHub.TS -gg -g1 -sf -srd -sreg -var "var.TSDir" -out "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments\TS.wxs"
```
**Note:** _If the TradeSharp backend was not cloned in C:\trade-nexus directory, update the -out path in the batch file above. It is also important that step # 2 is followed completely before proceeding with this step. C:\TradeSharp directory and the sub-dirctories should already be created with the required content._ 

 
**Running the batch file**

Save changes if any and follow the steps below.  

```
1. Launch the Command Prompt (press Win+R on your keyboard and then type cmd. Press Enter)
2. Enter the following command:
C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.LaunchConditions\TradeHub-Automated-Installer.bat
```

Result:

After successful execution the files at location "C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\Fragments” should be updated (check date modified).

--

**Step # 4: Building Code to Create TradeSharp Installer**

Open visual studio instance with TradeHub Backend code and switch to **release** mode from top menu.

1. In the Solution explorer, expand the **Installer** folder.
1. Right click on **TradeHub.Installer.Core** and click on properties.
1. On the screen that opens, select **Build** from the left menu.

Ensure “Define preprocessor variables” has the following content:

```
MyDir=C:\TradeSharp\MarketDataEngine;OEEDir=C:\TradeSharp\OrderExecutionEngine;PEDir=C:\TradeSharp\PositionEngine;UIDir=C:\TradeSharp\TradeHubGui;ISDir=C:\TradeSharp\Configuration;TMDir=C:\TradeSharp\TradeManager;TSDir=C:\TradeSharp\TemplateInstaller;
```

**Clean and Build TradeHub Installer**

1. Right click on **TradeHub.Installer.Core** and select **Clean**.
1. Right click on **TradeHub.Installer.Core** and select **Build**.

Once complete there should be a “TradeHub.Installer.msi” file at location 
C:\trade-nexus\tradesharp-core\Backend\Installer\TradeHub.Installer.Core\bin\Release\en-us

