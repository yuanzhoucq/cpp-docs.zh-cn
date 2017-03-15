---
title: "使用动态访问器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "访问器 [C++], dynamic"
  - "动态访问器"
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用动态访问器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

动态访问器使您可以在不了解数据库架构（基础结构）的情况下访问数据源。  OLE DB 模板库提供了若干个类来帮助您实现这一目标。  
  
 [DynamicConsumer](http://msdn.microsoft.com/zh-cn/2ccc4c61-6749-4e83-aa81-00f8009c0dc3) 示例显示如何使用动态访问器类获取列信息和动态创建访问器。  
  
## 使用 CDynamicAccessor  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  `CDynamicAccessor` 方法获取列信息，如列名、计数和数据类型。  使用该列信息在运行时动态创建访问器。  列信息存储在由该类创建并管理的缓冲区中。  使用 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) 方法从该缓冲区中获取数据。  
  
## 示例  
  
### 代码  
  
```  
// Using_Dynamic_Accessors.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
  
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
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            DBTYPE type;  
            rs.GetColumnType( i, &type );  
            printf_s( "Column %d [%S] is of type %d\n",  
                      i, rs.GetColumnName( i ), type );   
  
            switch( type )  
            {  
                case DBTYPE_WSTR:  
                    printf_s( "value is %S\n",  
                              (WCHAR*)rs.GetValue( i ) );  
                break;  
                case DBTYPE_STR:  
                    printf_s( "value is %s\n",  
                              (CHAR*)rs.GetValue( i ) );  
                default:  
                    printf_s( "value is %d\n",  
                              *(long*)rs.GetValue( i ) );  
            }  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
    return 0;  
}  
```  
  
## 使用 CDynamicStringAccessor  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) 的工作方式类似于 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，只是在一个重要方面有所差异。  `CDynamicAccessor` 请求提供程序以本机格式报告数据，而 `CDynamicStringAccessor` 则请求提供程序以字符串数据形式获取在数据存储区中存取的所有数据。  这对于不需要计算数据存储区中的值的简单任务（如显示或打印数据存储区的内容）很有用。  
  
 使用 `CDynamicStringAccessor` 方法获取列信息。  使用该列信息在运行时动态创建访问器。  该列信息存储在由此类创建并管理的缓冲区中。  使用 [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) 从此缓冲区中获取数据，或使用 [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md) 将数据存储到此缓冲区中。  
  
## 示例  
  
### 代码  
  
```  
// Using_Dynamic_Accessors_b.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
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
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            printf_s( "column %d value is %s\n",   
                      i, rs.GetString( i ) );  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
   return 0;  
  
}  
```  
  
## 使用 CDynamicParameterAccessor  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 类似于 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，不同之处在于 `CDynamicParameterAccessor` 通过调用 [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) 接口来获取要设置的参数信息。  提供程序必须支持 `ICommandWithParameters` 以便使用者使用该类。  
  
 参数信息存储在由该类创建并管理的缓冲区中。  通过使用 [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md) 从此缓冲区中获取参数数据。  
  
 有关说明如何使用该类执行 SQL Server 存储过程并获取输出参数值的示例，请参见知识库文章 Q058860“如何使用 CDynamicParameterAccessor 执行存储过程”。知识库文章可以在 MSDN Library Visual Studio 文档中或在 [http:\/\/support.microsoft.com](http://support.microsoft.com/)。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [DynamicConsumer Sample](http://msdn.microsoft.com/zh-cn/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)