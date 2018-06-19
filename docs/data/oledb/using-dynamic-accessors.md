---
title: 使用动态访问器 |Microsoft 文档
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 700a959742fafd4478659ff08821b043aff8bc14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111967"
---
# <a name="using-dynamic-accessors"></a>使用动态访问器

动态访问器，可以在不知道数据库架构 （基础结构） 时访问数据源。 OLE DB 模板库提供了几个类来帮助你执行此操作。

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例演示如何使用动态访问器类来获取列信息并动态创建访问器。

## <a name="using-cdynamicaccessor"></a>使用 CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)允许你访问数据源，当在不知道数据库架构 （数据库的基础结构）。 `CDynamicAccessor` 方法获取列信息，如列名称、 计数和数据类型。 此列信息用于在运行时动态创建取值函数。 列信息存储在缓冲区是创建和管理此类。 获取数据缓冲区使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)方法。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>使用 CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)工作方式类似于[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，除非在一个重要区别。 虽然`CDynamicAccessor`请求中提供程序，报告的本机格式数据`CDynamicStringAccessor`请求提供程序获取访问从数据存储区作为字符串数据的所有数据。 这是对于不需要计算的数据存储，例如显示或打印数据存储区的内容中的值的简单任务特别有用。

使用`CDynamicStringAccessor`方法以获取列信息。 此列信息用于在运行时动态创建取值函数。 列信息存储在缓冲区创建和管理此类。 获取数据缓冲区使用[cdynamicstringaccessor:: Getstring](../../data/oledb/cdynamicstringaccessor-getstring.md)或将其存储到缓冲区使用[cdynamicstringaccessor:: Setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>使用 CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)类似于[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，只不过`CDynamicParameterAccessor`获取参数信息，以通过调用设置[ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)接口。 访问接口必须支持 `ICommandWithParameters` 以便使用者使用此类。

参数信息存储在由此类创建和管理的缓冲区中。 使用从缓冲区中获取参数数据[cdynamicparameteraccessor:: Getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md)和[cdynamicparameteraccessor:: Getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)。

有关演示如何使用此类来执行 SQL Server 存储过程并获取输出参数值的示例，请参阅[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例中的代码[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)在 GitHub 上的存储库。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)  
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)  
[CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)  
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)  
[DynamicConsumer 示例](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)  
