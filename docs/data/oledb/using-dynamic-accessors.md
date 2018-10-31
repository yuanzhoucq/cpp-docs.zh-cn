---
title: 使用动态访问器 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: df80dfb235a03fdc45dfaa8a60c5fa5c1afb30bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053300"
---
# <a name="using-dynamic-accessors"></a>使用动态访问器

动态访问器，可以在不知道数据库架构 （基础结构） 时访问数据源。 OLE DB 模板库提供了几个类可帮助您。

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例演示如何使用动态访问器类来获取列信息和动态创建访问器。

## <a name="using-cdynamicaccessor"></a>使用 CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ，可在不知道数据库架构 （数据库的基础结构） 时访问数据源。 `CDynamicAccessor` 方法获取列信息，例如列名称、 计数和数据类型。 此列信息用于在运行时动态创建取值函数。 列信息存储在缓冲区的创建和管理此类。 从缓冲区使用获取数据[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)方法。

## <a name="example"></a>示例

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

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)工作方式类似于[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，重要的一种方法中除外。 虽然`CDynamicAccessor`请求数据以本机格式提供程序，报告`CDynamicStringAccessor`请求提供程序提取从字符串数据作为数据存储区访问的所有数据。 该过程是对于不需要计算的数据存储，如在显示或输出数据存储区的内容中的值的简单任务特别有用。

使用`CDynamicStringAccessor`方法来获取列信息。 此列信息用于在运行时动态创建取值函数。 创建和管理此类缓冲区中存储的列信息。 从缓冲区使用获取数据[cdynamicstringaccessor:: Getstring](../../data/oledb/cdynamicstringaccessor-getstring.md)或将其存储到缓冲区使用[cdynamicstringaccessor:: Setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)。

## <a name="example"></a>示例

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

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)类似于[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，只不过`CDynamicParameterAccessor`获取参数信息将通过调用[ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters)接口。 访问接口必须支持 `ICommandWithParameters` 以便使用者使用此类。

参数信息存储在由此类创建和管理的缓冲区中。 通过使用从缓冲区获取参数数据[cdynamicparameteraccessor:: Getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md)并[cdynamicparameteraccessor:: Getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)。

有关演示如何使用此类以执行 SQL Server 存储过程并获取输出参数值的示例，请参阅[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例中的代码[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)GitHub 上的存储库。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer 示例](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
