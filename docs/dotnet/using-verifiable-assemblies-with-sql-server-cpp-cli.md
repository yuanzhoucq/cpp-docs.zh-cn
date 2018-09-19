---
title: 使用 SQL Server 可验证程序集 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbd42d3d51921ccab01dfdcaed9ad988e22ae9a8
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894698"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>结合使用 SQL Server 和可验证的程序集 (C++/CLI)

扩展存储的过程，打包为动态链接库 (Dll)，提供一种方法来扩展 SQL Server 功能，通过使用 Visual c + + 开发的函数。 扩展存储的过程将作为 Dll 中的函数。 除了函数外，还可以定义扩展存储的过程[用户定义类型](../cpp/classes-and-structs-cpp.md)和聚合函数 （如 SUM 或 AVG）。

当客户端执行扩展存储的过程时，SQL Server DLL 的搜索与扩展存储过程相关联，并加载此 DLL。 SQL Server 调用请求的扩展存储的过程，并指定的安全上下文下执行。 扩展存储，然后传递结果集，并将参数返回给服务器的过程。

SQL Server transact-sql (T-SQL) 以允许你可验证程序集安装到 SQL Server 中提供的扩展。 SQL Server 的权限集指定安全上下文中，具有以下级别的安全性：

- 不受限制的模式： 您自己承担; 运行代码代码不需要是可验证类型安全的。

- 安全模式： 运行可验证类型安全代码;使用 /clr: safe 编译。

安全模式下需要执行的程序集是可验证类型安全。

若要创建和可验证的程序集加载到 SQL Server，请使用 TRANSACT-SQL 命令创建程序集和删除程序集，如下所示：

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```  

PERMISSION_SET 命令指定安全上下文中，且可以具有不受限制的、 安全的或扩展的值。

此外，您可以使用 CREATE FUNCTION 命令将绑定到类中的方法名称：

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```  

## <a name="example"></a>示例
以下 SQL 脚本 (例如，名为"MyScript.sql") 将程序集加载到 SQL Server，并使类的方法可用：

```sql
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

在 SQL 查询分析器或在命令行使用 sqlcmd.exe 实用工具，可以以交互方式执行 SQL 脚本。 下面的命令行连接到 MyServer、 使用的默认数据库，使用可信的连接、 输入 MyScript.sql，并输出 MyResult.txt。

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```  

## <a name="see-also"></a>请参阅

[如何： 将迁移到 /clr: safe (C + + CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
[类和结构](../cpp/classes-and-structs-cpp.md)