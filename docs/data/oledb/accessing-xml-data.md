---
title: "访问 XML 数据 | Microsoft Docs"
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
  - "CStreamRowset 类, 检索 XML 数据"
  - "CXMLAccessor 类, 检索 XML 数据"
  - "数据 [C++], XML 数据访问"
  - "数据访问 [C++], XML 数据"
  - "行集合 [C++], 检索 XML 数据"
  - "XML [C++], 访问数据"
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 访问 XML 数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从数据源检索 XML 数据有两种不同的方法：一种方法使用 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)，另一种方法使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  
  
|功能|CStreamRowset|CXMLAccessor|  
|--------|-------------------|------------------|  
|传输的数据量|同时从所有列和行中检索数据。|一次仅从一行的所有列中检索数据。  必须使用 `MoveNext` 之类的方法定位行。|  
|格式化字符串|SQL Server 格式化 XML 字符串，并将其发送到使用者。|以其本机格式检索行集合数据（请求提供程序将其作为 Unicode 字符串发送），然后以 XML 格式生成包含该数据的字符串。|  
|对格式化加以控制|可以通过设置某些 SQL Server 2000 特定的属性对格式化 XML 字符串的方式具有某一级别的控制权。|您对生成的 XML 字符串的格式没有控制权。|  
  
 尽管 `CStreamRowset` 为检索 XML 格式数据提供了一种总体上较为有效的方法，但只有 SQL Server 2000 支持该方法。  
  
## 使用 CStreamRowset 检索 XML 数据  
 在 `CCommand` 或 `CTable` 声明中将 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 指定为行集合类型。  可以将它与自己的访问器一起使用，也可以不与任何访问器一起使用，例如：  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 \- 或 \-  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 通常，调用 `CCommand::Open`（例如，将 `CRowset` 指定为 `TRowset` 类）时，它会获取一个 `IRowset` 指针。  `ICommand::Execute` 会返回一个 `IRowset` 指针，该指针存储在 `CRowset` 对象的 `m_spRowset` 成员中。  `MoveFirst`、`MoveNext` 和 `GetData` 等方法使用该指针检索数据。  
  
 相反，调用 `CCommand::Open`（不过，将 `CStreamRowset` 指定为 `TRowset` 类）时，`ICommand::Execute` 会返回一个 `ISequentialStream` 指针，该指针存储在 [CStreamRowset](../../data/oledb/cstreamrowset-class.md) 的 `m_spStream` 数据成员中。  然后，您可以使用 `Read` 方法检索 XML 格式的（Unicode 字符串）数据。  例如：  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 执行 XML 格式化，并将行集合的所有列和所有行作为一个 XML 字符串返回。  
  
 有关使用 `Read` 方法的示例，请参见[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)中的“向使用者中添加 XML 支持”。  
  
> [!NOTE]
>  使用 `CStreamRowset` 的 XML 支持仅适用于 SQL Server 2000，并且要求具有用于 SQL Server 2000 的 OLE DB 提供程序（与 MDAC 一起安装）。  
  
## 使用 CXMLAccessor 检索 XML 数据  
 如果您不了解有关数据存储架构的知识，则可以使用 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) 以字符串数据的形式访问数据源中的数据。  `CXMLAccessor` 的工作原理与 `CDynamicStringAccessorW` 类似，不过，前者会将从数据存储访问的所有数据都转换为 XML 格式的（即带标记的）数据。  XML 标记名会尽可能与数据存储区的列名匹配。  
  
 与使用其他任何访问器类一样使用 `CXMLAccessor`，并将其作为模板参数传递到 `CCommand` 或 `CTable`：  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 使用 [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) 从表中逐行检索数据，并使用 `MoveNext` 之类的方法定位行，例如：  
  
```  
// Open data source, session, and rowset  
hr = rs.MoveFirst();  
while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
{  
    CStringW strRowData;  
    myCmd.GetXMLRowData(strRowData);  
  
    printf_s( "%S\n", strRowData );  
  
    hr = rs.MoveNext();  
}  
```  
  
 可以使用 [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) 将列（数据类型）信息作为 XML 格式化字符串数据进行检索。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)