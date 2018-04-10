---
title: 使用 SQL Server 可验证程序集 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d03d54dd52f95f3fbba35bb896594e90aa92e867
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>结合使用 SQL Server 和可验证的程序集 (C++/CLI)
扩展存储的过程，打包为动态链接库 (Dll)，提供一种方法来扩展通过使用 Visual c + + 开发的函数的 SQL Server 功能。 扩展存储的过程实现为 Dll 中的函数。 除了函数外，还可以定义扩展存储的过程[用户定义的类型](../cpp/classes-and-structs-cpp.md)和[聚合函数](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da)（如 SUM 或 AVG）。  
  
 当客户端执行扩展存储的过程时，SQL Server 中的 dll 的搜索与扩展存储过程并加载 DLL。 SQL Server 调用请求的扩展存储的过程，并在指定的安全上下文下执行它。 扩展存储然后传递结果集，并将参数返回到服务器的过程。  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)]提供对 TRANSACT-SQL (T-SQL) 以便您可以将可验证程序集安装到 SQL Server 扩展。 SQL Server 权限集指定安全上下文中，具有以下级别的安全性：  
  
-   不受限制的模式： 在你自己的风险; 运行的代码不必是可验证类型安全代码。  
  
-   安全模式下： 运行可验证类型安全代码;使用 /clr: safe 编译。  
  
 安全模式下需要执行的程序集是可验证类型安全。  
  
 若要创建和可验证的程序集加载到 SQL Server，使用 TRANSACT-SQL 命令创建程序集和 DROP ASSEMBLY，如下所示：  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 PERMISSION_SET 命令指定安全上下文中，并且可以具有不受限制的、 安全的或扩展的值。  
  
 此外，你可以使用 CREATE FUNCTION 命令要绑定到类中的方法名称：  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>示例  
 以下 SQL 脚本 (例如，名为"MyScript.sql") 将程序集加载到 SQL Server，并提供一个类的方法：  
  
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
  
 在 SQL 查询分析器或在命令行使用 sqlcmd.exe 实用程序，可以以交互方式执行 SQL 脚本。 下面的命令行连接到 MyServer、 使用的默认数据库，使用可信的连接，输入 MyScript.sql，并输出 MyResult.txt。  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>请参阅  
 [如何： 将迁移到 /clr: safe (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [类和结构](../cpp/classes-and-structs-cpp.md)