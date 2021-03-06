---
title: 设置 SQL Server 上的 R 开发数据科学客户端 |Microsoft Docs
description: 远程连接到 SQL Server 的开发工作站上安装本地 R 库和工具。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/12/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 087d7249fbcbb206566e822c634f10e8bc4ba838
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703148"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>设置 SQL Server 上的 R 开发数据科学客户端
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R 集成是提供的 SQL Server 2016 或更高版本包括中的 R 语言选项时[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)或[SQL Server 2017 机器学习服务 （数据库内）](../install/sql-machine-learning-services-windows-install.md)安装。 

若要创建和部署 SQL Server 上的 R 解决方案，安装[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)若要获取[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)以及在开发工作站上的其他 R 库。 RevoScaleR 库，也是远程的 SQL Server 实例上，可协调计算这两个系统之间的请求。 

在本文中，了解如何配置 R 客户端开发工作站，以便可以连接到远程 SQL Server 启用了机器学习和 R 集成。 完成这篇文章中的步骤后，将具有与 SQL Server 上的同一 R 库。 此外将了解如何将计算从本地 R 会话的远程 R 会话到推送 SQL Server 上。

![客户端-服务器组件](media/sqlmls-r-client-revo.png "本地和远程 R 会话和库")

可以使用内置**RGUI**工具在本文中所述或[链接库](#install-ide)到 RStudio 或任何你通常使用的另一个 IDE。

> [!Tip]
> 这些练习的视频演示，请参阅[运行 R 和 Python 在 Jupyter Notebook 从 SQL Server 中远程](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/)。

> [!Note]
> 使用客户端库安装的替代方法[独立服务器](../install/sql-machine-learning-standalone-windows-install.md)为丰富客户端，有些客户更喜欢更深层次的方案中工作。 从 SQL Server 完全分离的独立服务器，但因其具有相同的 R 库，你可以使用它作为客户端的 SQL Server 数据库内分析。 您还可以使用它为非 SQL 相关的工作，包括导入和从其他数据平台的数据建模功能。 如果安装在独立服务器，可以找到 R 可执行文件位于以下位置： `C:\Program Files\Microsoft SQL Server\140\R_SERVER`。 若要验证你的安装，[打开 R 控制台应用](#R-tools)运行在该位置使用 R.exe 命令。

## <a name="commonly-used-tools"></a>常用工具

无论您是熟悉 SQL，R 开发人员或 SQL 开发人员首次使用 R 和数据库内分析，您将需要 R 开发工具和 T-SQL 查询编辑器等[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)以实现所有数据库内分析功能。

对于简单的 R 开发方案，使用可执行文件，RGUI 捆绑在一起在 MRO 和 SQL Server 基础 R 发行版中。 此文章介绍了如何对本地和远程 R 会话使用 RGUI。 为提高工作效率，您应使用全功能型 IDE 如[RStudio 或 Visual Studio](#install-ide)。

SSMS 是单独的下载，适用于创建和上 SQL Server，包括那些包含 R 代码运行存储的过程。 在开发环境中编写的几乎任何 R 代码可以嵌入在存储过程。 您可以单步执行其他教程，了解如何[SSMS 和嵌入的 R](../tutorials/sqldev-in-database-r-for-sql-developers.md)。

## <a name="1---install-r-packages"></a>1-安装 R 包

Microsoft 的 R 包有多个产品和服务。 在本地工作站上，我们建议安装 Microsoft R 客户端。 R 客户端提供了[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)， [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)， [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)，和其他 R 包。

1. [下载 Microsoft R 客户端](https://aka.ms/rclient/download)。

2. 在安装向导中，接受或更改默认安装路径、 接受或更改的组件列表，并接受 Microsoft R Client 许可条款。

完成安装后，一个欢迎屏幕，向您介绍的产品和文档。

在 R 客户端，R 处理上限为两个线程和内存中的数据。 对于使用多个内核和大型数据集的可缩放处理，你可以上移执行 (称为*计算上下文*) 到数据集和计算能力的远程 SQL Server 实例。 这是客户端集成与生产 SQL Server 实例的推荐的方法。 

## <a name="2---locate-executables"></a>2-查找可执行文件

找到并列出要确认 R.exe、 RGUI 和其他包安装的安装文件夹的内容。 

1. 在文件资源管理器，打开 C:\Program Files\Microsoft\R Client\R_SERVER\bin 文件夹，以确认 R.exe 的位置。

2. 打开 x64 子文件夹，用于确认**RGUI**。

3. 打开 C:\Program Files\Microsoft\R Client\R_SERVER\library，若要查看使用 R 客户端，包括 RevoScaleR、 MicrosoftML，和其他安装的包的列表。


<a name="r-tool"></a>
 
## <a name="3---start-rgui"></a>3-启动 RGUI

使用 SQL Server 安装 R，可以获取相同的 R 工具的标准到 R，例如 RGui 和 Rterm，等任何基本安装。 这些工具是轻量，可用于检查包和库的信息、 运行临时命令或脚本，或逐步执行教程。 这些工具可用于获取 R 版本信息，并确认连接。

1. 打开 C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64，然后双击**RGui**若要使用 R 命令提示符启动 R 会话。

  从 Microsoft 程序文件夹中，多个包，包括 RevoScaleR，启动 R 会话时自动加载。 

2. 输入`print(Revo.version)`在命令提示符下，返回 RevoScaleR 包版本信息。 对于 RevoScaleR，应具有版本 9.2.1 或 9.3.0。

3. 输入**search （)** 在 R 提示符有关已安装的包的列表。

   ![版本信息时加载 R](../install/media/rclient-rgui-r-prompt.png "打开 R 提示符")


## <a name="4---get-sql-permissions"></a>4-获取 SQL 权限

若要连接到要运行脚本和上传数据的 SQL Server 实例，必须在数据库服务器上具有有效的登录名。 可以使用 SQL 登录凭据或集成 Windows 身份验证信息。 我们通常建议使用 Windows 集成身份验证，但使用 SQL 登录名是在某些情况下，更简单，尤其是在脚本中包含对外部数据连接字符串时。

最小值，用来运行代码的帐户必须具有你正在使用，加上特殊权限执行任意外部脚本从数据库中读取的权限。 大多数开发人员还需要权限才能创建存储的过程，并将数据写入到包含训练数据的表或评分的数据。 

询问数据库管理员来[配置你的帐户的以下权限](../security/user-permission.md)，其中使用： 在数据库中

+ **EXECUTE ANY EXTERNAL SCRIPT**若要在服务器上运行 R 脚本。
+ **db_datareader**权限才能运行用于定型模型的查询。
+ **db_datawriter**编写定型数据或评分的数据。
+ **db_owner**以创建对象的存储过程，如表、 函数。 
  您还需要**db_owner**创建示例，并测试数据库。 

如果你的代码需要与 SQL Server 的默认情况下不安装的程序包，排列与数据库管理员能够与实例安装的包。 SQL Server 是一个受保护的环境并在其中安装包的限制。 有关详细信息，请参阅[SQL Server 上安装新的 R 包](install-additional-r-packages-on-sql-server.md)。

## <a name="5---test-connections"></a>5-测试连接

 作为验证步骤，使用**RGUI**和 RevoScaleR 以确认连接到远程服务器。 必须启用 SQL Server[远程连接](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md)并且必须具有的权限，包括用户登录名和要连接到数据库。 

下面的步骤假定演示数据库[NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)，和 Windows 身份验证。

1. 打开**RGUI**客户端工作站上。 例如，请转到`~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`，然后双击**RGui.exe**来启动它。

2. RevoScaleR 会自动加载。 确认 RevoScaleR 可以正常运行的通过运行以下命令： `print(Revo.version)`

3. 输入远程服务器执行的演示脚本。 必须修改下面的示例脚本，包括远程 SQL Server 实例的有效名称。 此会话开始作为本地会话，但**rxSummary**函数执行的远程 SQL Server 实例上。

  ```r
  # Define a connection. Replace server with a valid server name.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  
  # Specify the input data in a SQL query.
  sampleQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
  
  # Define a remote compute context based on the remote server.
  cc <-RxInSqlServer(connectionString=connStr)

  # Execute the function using the remote compute context.
  rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr), computeContext=cc)
  ```

  **结果：**

  此脚本连接到远程服务器上的数据库，提供查询、 创建计算上下文`cc`指令的远程执行代码，然后提供的 RevoScaleR 函数**rxSummary**返回统计查询结果的摘要。

  ```r
    Call:
  rxSummary(formula = ~., data = RxSqlServerData(sqlQuery = sampleQuery, 
      connectionString = connStr), computeContext = cc)

  Summary Statistics Results for: ~.
  Data: RxSqlServerData(sqlQuery = sampleQuery, connectionString = connStr) (RxSqlServerData Data Source)
  Number of valid observations: 100 
  
  Name       Mean   StdDev   Min Max ValidObs MissingObs
  tip_amount 63.245 31.61087 36  180 100      0     
  ```

4. 获取和设置计算上下文。 一旦设置计算上下文，它将保持有效的会话的持续时间。 如果不确定计算是本地还是远程，运行以下命令以找出。指定连接字符串的结果指示远程计算上下文。

  ```r
  # Return the current compute context.
  rxGetComputeContext()

  # Revert to a local compute context.
  rxSetComputeContext("local")
  rxGetComputeContext()

  # Switch back to remote.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  cc <-RxInSqlServer(connectionString=connStr)
  rxSetComputeContext(cc)
  rxGetComputeContext()
  ```  

5. 数据源，包括名称和类型中返回变量的信息。

  ```r
  rxGetVarInfo(data = inDataSource)
  ```
  结果包含 23 变量。


6. 生成散点图以了解是否有两个变量之间的依赖项。 

  ```r
  # Set the connection string. Substitute a valid server name for the placeholder.
  connStr <- "Driver=SQL Server;Server=<your database name>;Database=NYCTaxi_Sample;Trusted_Connection=true"

  # Specify a query on the nyctaxi_sample table.
  # For variables on each axis, remove nulls. Use a WHERE clause and <> to do this.
  sampleQuery <-"SELECT DISTINCT TOP 100 * from [dbo].[nyctaxi_sample] WHERE fare_amount <> '' AND  tip_amount <> ''"
  cc <-RxInSqlServer(connectionString=connStr)

  # Generate a scatter plot.
  rxLinePlot(fare_amount ~ tip_amount, data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr, computeContext=cc), type="p")
  ```

  下面的屏幕截图显示了输入和散点图输出。

   ![散点图中 RGUI](media/rclient-setup-scatterplot.png "NYC 出租车演示数据上的散点图")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6-链接到 R.exe 工具

对于持续和严重开发项目，则应安装集成的开发环境 (IDE)。 SQL Server 工具和内置的 R 工具未配备繁重的 R 开发中。 工作代码后，可以将其部署为 SQL Server 上执行的存储过程。

你的 IDE 指向本地 R 库： 基本 R、 RevoScaleR，等等。 远程 SQL 服务器上运行的工作负荷执行脚本期间发生，当您的脚本调用访问数据和操作该服务器上的 SQL 服务器上的远程计算上下文。

### <a name="rstudio"></a>RStudio

使用时[RStudio](https://www.rstudio.com/)，可以配置要使用的 R 库和对应于远程 SQL 服务器上的可执行文件的环境。

1. 检查 SQL Server 上安装 R 包版本。 有关详细信息，请参阅[获取 R 包信息](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)。

1. 安装 Microsoft R 客户端或独立服务器选项，以添加 RevoScaleR 和其他 R 包，包括 SQL Server 实例使用的基础 R 发行版之一。 选择在同一版本级别或更低 （包是向后兼容） 的服务器上提供相同的包版本。 有关版本信息，请参阅这篇文章中映射的版本：[升级 R 和 Python 组件](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)。

1. 在 RStudio 中，[更新 R 路径](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R)以指向提供 RevoScaleR、 Microsoft R Open，以及其他 Microsoft 包的 R 环境。 

  + 对于 R 客户端安装，查找 C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64
  + 对于独立服务器，查找 C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library 或 C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. 关闭，然后打开 RStudio。

当你重新打开 RStudio 时，R 可执行文件从 R 客户端 （或独立服务器） 是默认 R 引擎。


### <a name="r-tools-for-visual-studio-rtvs"></a>R Tools for Visual Studio (RTVS)

如果你还没有首选的 IDE 适用于 R，我们建议**针对 Visual Studio 的 R 工具**。

+ [下载 R Tools for Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [安装说明](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio)-RTVS 是在多个 Visual Studio 版本中可用。
+ [入门 Visual Studio 的 R 工具](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>从 RTVS 连接到 SQL Server

此示例使用 Visual Studio 2017 Community Edition 已安装数据科学工作负载。

1. 从**文件**菜单中，选择**新建**，然后选择**项目**。

2. 在左侧窗格列出了预安装的模板。 单击**R**，然后选择**R 项目**。 在中**名称**框中，键入`dbtest`然后单击**确定**。 

  Visual Studio 将创建一个新的项目文件夹和默认脚本文件， `Script.R`。 

3. 类型`.libPaths()`脚本的第一行上文件，，然后按 CTRL + ENTER。

  当前的 R 库路径应显示在**R 交互**窗口。 

4. 单击**的 R 工具**菜单，然后选择**Windows**若要查看其他特定于 R 的窗口都可以在你的工作区中显示的列表。
 
  + 通过按 CTRL + 3 查看当前存储库中的包上的帮助。
  + 请参阅中的 R 变量**变量资源管理器**，通过按 CTRL + 8。

## <a name="next-steps"></a>后续步骤

两个不同教程包括练习，以便您可以练习切换到远程 SQL Server 实例从本地计算上下文。

+ [教程： 使用 RevoScaleR R 函数与 SQL Server 数据](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [数据科学端到端演练](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)