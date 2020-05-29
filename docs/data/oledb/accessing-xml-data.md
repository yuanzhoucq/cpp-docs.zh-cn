---
title: 访问 XML 数据
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: be4225003211449a98d3fbe5fd686b9b8058a651
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212272"
---
# <a name="accessing-xml-data"></a>访问 XML 数据

可以通过两种不同的方法从数据源中检索 XML 数据：一个使用[CStreamRowset](../../data/oledb/cstreamrowset-class.md) ，另一个使用[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)。

|功能|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|传输的数据量|同时检索所有列和行中的数据。|检索所有列中的数据，但一次只能检索一行。 必须使用 `MoveNext`等方法来浏览行。|
|设置字符串格式|SQL Server 格式化 XML 字符串并将其发送给使用者。|检索以本机格式表示的行集数据（请求提供程序将其作为 Unicode 字符串发送），然后生成保存 XML 格式的数据的字符串。|
|控制格式设置|通过设置某些 SQL Server 2000 特定的属性，可以对 XML 字符串的格式设置进行一定程度的控制。|你无法控制生成的 XML 字符串的格式。|

虽然 `CStreamRowset` 提供了一种更有效的方法来检索 XML 格式的数据，但它仅受 SQL Server 2000 的支持。

## <a name="retrieving-xml-data-using-cstreamrowset"></a>使用 CStreamRowset 检索 XML 数据

在 `CCommand` 或 `CTable` 声明中指定[CStreamRowset](../../data/oledb/cstreamrowset-class.md)作为行集类型。 你可以将其与你自己的访问器或无访问器一起使用，例如：

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-或-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

通常，当调用 `CCommand::Open` （例如，将 `CRowset` 指定为 `TRowset` 类）时，它将获取 `IRowset` 指针。 `ICommand::Execute` 返回 `IRowset` 指针，该指针存储在 `CRowset` 对象的 `m_spRowset` 成员中。 `MoveFirst`、`MoveNext`和 `GetData` 等方法使用该指针检索数据。

与此相反，当您调用 `CCommand::Open` （但将 `CStreamRowset` 指定为 `TRowset` 类）时，`ICommand::Execute` 返回 `ISequentialStream` 指针，该指针存储在[CStreamRowset](../../data/oledb/cstreamrowset-class.md)的 `m_spStream` 数据成员中。 然后，使用 `Read` 方法以 XML 格式检索（Unicode 字符串）数据。 例如：

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 执行 XML 格式设置，并返回行集的所有列和所有行作为一个 XML 字符串。

有关使用 `Read` 方法的示例，请参阅[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)中**的向使用者添加 XML 支持**。

> [!NOTE]
> 使用 `CStreamRowset` 的 XML 支持仅适用于 SQL Server 2000，并且需要具有 SQL Server 2000 的 OLE DB 提供程序（随 MDAC 一起安装）。

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>使用 CXMLAccessor 检索 XML 数据

当你不知道数据存储的架构时， [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)允许你以字符串数据的形式访问数据源中的数据。 `CXMLAccessor` 的工作方式类似于 `CDynamicStringAccessorW`，只不过前者会将从数据存储访问的所有数据都转换为 XML 格式（标记）的数据。 XML 标记名称与数据存储区的列名尽可能匹配。

像对待任何其他访问器类一样使用 `CXMLAccessor`，并将其作为模板参数传递到 `CCommand` 或 `CTable`：

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

使用[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)从表中一次检索一次数据，并使用 `MoveNext`等方法浏览行，例如：

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

可以使用[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)以 XML 格式的字符串数据的形式检索列（数据类型）信息。

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
