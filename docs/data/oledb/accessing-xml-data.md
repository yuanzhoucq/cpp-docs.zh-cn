---
title: 访问 XML 数据 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: d7db1d790ca9caeea6bd9c7853139f59ffa0ab6c
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808714"
---
# <a name="accessing-xml-data"></a>访问 XML 数据

从数据源中检索 XML 数据的两种不同方法： 一个使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md)和其他用途[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。  
  
|功能|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|传输的数据量|立即从所有列和行中检索数据。|从所有列中的检索数据，但一次只有一个行。 必须导航使用方法，如行`MoveNext`。|  
|格式化字符串|SQL Server 格式的 XML 字符串，并将其发送给使用者。|检索以本机格式 （提供程序将作为 Unicode 字符串发送的请求） 的行集数据，然后生成 XML 格式保存数据的字符串。|  
|控制格式设置|具有某些级别的控制如何通过设置某些特定于 SQL Server 2000 的属性设置的 XML 字符串的格式。|你可以不控制生成的 XML 字符串的格式。|  
  
虽然`CStreamRowset`能在 XML 格式检索数据的多个整体高效的方式仅受 SQL Server 2000。  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 中检索 XML 数据  

您指定[CStreamRowset](../../data/oledb/cstreamrowset-class.md)中的行集类型为您`CCommand`或`CTable`声明。 您可以使用它自己的访问器或没有访问器，例如：  
  
```cpp  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
或  
  
```cpp  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
通常情况下调用`CCommand::Open`(指定，例如，`CRowset`作为`TRowset`类)，它获取`IRowset`指针。 `ICommand::Execute` 返回`IRowset`指针，它存储在`m_spRowset`的成员`CRowset`对象。 等方法`MoveFirst`， `MoveNext`，和`GetData`使用该指针来检索数据。  
  
与此相反，当您调用`CCommand::Open`(但指定`CStreamRowset`作为`TRowset`类)，`ICommand::Execute`返回`ISequentialStream`指针，它存储在`m_spStream`的数据成员[CStreamRowset](../../data/oledb/cstreamrowset-class.md). 然后，使用`Read`方法来检索 XML 格式 （Unicode 字符串） 的数据。 例如：  
  
```cpp  
myCmd.m_spStream->Read()  
```  
  
SQL Server 2000 进行 XML 格式化，并返回所有列和行集作为一个 XML 字符串的所有行。  
  
有关使用示例`Read`方法，请参阅中的"添加 XML 支持向使用者"[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)。  
  
> [!NOTE]
> XML 支持使用`CStreamRowset`仅适用于 SQL Server 2000 和要求的 SQL Server 2000 （安装与 MDAC） 具有 OLE DB 访问接口。  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 中检索 XML 数据  

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)允许您在不知道数据存储区的架构时从数据源作为字符串数据访问数据。 `CXMLAccessor` 工作方式类似于`CDynamicStringAccessorW`不同之处在于前者将转换从数据存储为 XML 格式 （标记） 的数据访问的所有数据。 XML 标记名称与尽可能接近地匹配数据存储区的列名称。  
  
使用`CXMLAccessor`就像任何其他访问器类，将其作为传递到一个模板参数`CCommand`或`CTable`:  
  
```cpp  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)表的某一行中检索数据，一次，并导航使用方法，如行`MoveNext`，例如：  
  
```cpp  
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
  
可以使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)检索 XML 格式的字符串数据与列 （数据类型） 的信息。  
  
## <a name="see-also"></a>请参阅  

[使用访问器](../../data/oledb/using-accessors.md)