---
title: 访问 XML 数据 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f3abe00adee2a88d0414d688984232422a5bcfc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-xml-data"></a>访问 XML 数据
有从数据源中检索 XML 数据的两个不同方法： 另一个使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md)和其他用途[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  
  
|功能|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|传输的数据量|从所有列和行中同时检索数据。|检索所有列中的数据，但一次只有一个行。 你必须导航行使用方法如`MoveNext`。|  
|格式字符串|SQL Server 设置 XML 字符串的格式，并将其发送给使用者。|检索行集数据以本机格式 （提供程序将其作为 Unicode 字符串发送的请求），然后生成包含 XML 格式的数据的字符串。|  
|控制格式设置|具有一定程度的控制如何通过设置某些特定于 SQL Server 2000 的属性设置的 XML 字符串的格式。|你不具有对控制生成的 XML 字符串的格式。|  
  
 虽然`CStreamRowset`提供检索 XML 格式的数据的多个总体高效方法仅受 SQL Server 2000。  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 中检索 XML 数据  
 你指定[CStreamRowset](../../data/oledb/cstreamrowset-class.md)中的行集类型作为你`CCommand`或`CTable`声明。 你可以将它与你自己的访问器或没有访问器，例如：  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 -或-  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 通常当调用`CCommand::Open`(指定，例如，`CRowset`作为`TRowset`类)，它获取`IRowset`指针。 `ICommand::Execute` 返回`IRowset`指针，它存储在`m_spRowset`的成员`CRowset`对象。 等方法`MoveFirst`， `MoveNext`，和`GetData`使用该指针来检索数据。  
  
 与此相反，当调用`CCommand::Open`(但指定`CStreamRowset`作为`TRowset`类)，`ICommand::Execute`返回`ISequentialStream`指针，它存储在`m_spStream`数据成员的[CStreamRowset](../../data/oledb/cstreamrowset-class.md). 然后，你使用`Read`方法来检索 XML 格式 （Unicode 字符串） 的数据。 例如：  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 执行 XML 格式，并返回所有列和行集作为一个 XML 字符串的所有行。  
  
 有关使用示例`Read`方法，请参阅中的"添加 XML 支持向使用者"[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
> [!NOTE]
>  XML 支持使用`CStreamRowset`仅适用于 SQL Server 2000 和，你需要具有 OLE DB 访问接口为 SQL Server 2000 （随 MDAC 一起安装）。  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 中检索 XML 数据  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)允许你在数据存储区架构不知道时从数据源作为字符串数据访问数据。 `CXMLAccessor` 工作方式类似于`CDynamicStringAccessorW`之处在于前者将转换从数据存储为 XML 格式 （有标记） 数据访问的所有数据。 XML 标记名称与尽可能地匹配数据存储区的列名称。  
  
 使用`CXMLAccessor`就像任何其他访问器类，则将其传递作为模板参数传递给`CCommand`或`CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)一次表某一行中检索数据，并导航行使用方法如`MoveNext`，例如：  
  
```  
// Open data source, session, and rowset  
hr = rs.MoveFirst();  

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
{  
    CStringW strRowData;  
    myCmd.GetXMLRowData(strRowData);  
  
    printf_s( "%S\n", strRowData );  
  
    hr = rs.MoveNext();  
}  
```  
  
 你可以使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)检索 XML 格式的字符串数据与列 （数据类型） 的信息。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)