---
title: "结合使用 SQL Server 和可验证的程序集 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "可验证程序集 [C++], 使用 SQL Server"
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 结合使用 SQL Server 和可验证的程序集 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

打包为动态链接库 \(DLL\) 的扩展存储过程提供一种方法，通过用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 开发的函数来扩展 SQL Server 功能。  扩展存储过程实现为 DLL 中的函数。  除函数外，扩展存储过程还可以定义[用户定义类型](../cpp/classes-and-structs-cpp.md)和[聚合函数](http://msdn.microsoft.com/zh-cn/de255454-f45e-4281-81f9-bc61893ac5da)（如 SUM 或 AVG）。  
  
 当客户端执行扩展存储过程时，SQL Server 搜索与扩展存储过程关联的 DLL 并加载该 DLL。  SQL Server 在指定的安全上下文下调用并执行所请求的扩展存储过程。  然后，扩展存储过程传递结果集并将参数返回给服务器。  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)] 提供了对 Transact\-SQL \(T\-SQL\) 的扩展，以允许将可验证的程序集安装到 SQL Server 中。  SQL Server 权限集指定安全上下文，其具有的安全级别如下：  
  
-   无限制模式：运行代码时风险自负；代码不必是可验证类型安全的。  
  
-   安全模式：运行可验证类型安全的代码；使用 \/clr:safe 编译。  
  
 安全模式要求执行的程序集是可验证类型安全的。  
  
 若要创建可验证程序集并将其加载到 SQL Server 中，请使用 Transact\-SQL 命令 CREATE ASSEMBLY 和 DROP ASSEMBLY，如下所示：  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 PERMISSION\_SET 命令指定安全上下文，其值可以为 UNRESTRICTED、SAFE 或 EXTENDED。  
  
 此外，还可以使用 CREATE FUNCTION 命令绑定到类中的方法名称：  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## 示例  
 下面的 SQL 脚本（例如，名为“MyScript.sql”）将程序集加载到 SQL Server 中并使类的方法可用：  
  
```  
-- Create assembly without external access  
drop assembly stockNoEA  
go  
create assembly stockNoEA  
from   
'c:\stockNoEA.dll'  
with permission_set safe  
  
-- Create function on assembly with no external access  
drop function GetQuoteNoEA  
go  
create function GetQuoteNoEA(@sym nvarchar(10))  
returns real  
external name stockNoEA:StockQuotes::GetQuote  
go  
  
-- To call the function  
select dbo.GetQuoteNoEA('MSFT')  
go  
```  
  
 SQL 脚本可以在 SQL 查询分析器中以交互方式执行，或在命令行下用 sqlcmd.exe 实用工具执行。  下面的命令行连接到 MyServer，使用默认的数据库和受信任的连接，输入 MyScript.sql，输出 MyResult.txt。  
  
```  
sqlcmd –S MyServer -E –i myScript.sql –o myResult.txt  
```  
  
## 请参阅  
 [如何：迁移到 \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [类和结构](../cpp/classes-and-structs-cpp.md)