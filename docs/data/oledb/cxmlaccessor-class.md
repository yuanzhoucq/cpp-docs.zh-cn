---
title: CXMLAccessor 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211037"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 类

当您不知道数据存储的架构（基础结构）时，允许您以字符串数据的形式访问数据源。

## <a name="syntax"></a>语法

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>要求

**标头**：atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|检索列信息。|
|[GetXMLRowData](#getxmlrowdata)|按行检索表的全部内容。|

## <a name="remarks"></a>备注

但 `CXMLAccessor` 与 `CDynamicStringAccessorW` 不同，因为它会将从数据存储访问的所有数据转换为 XML 格式（标记）的数据。 这对于输出到 XML 感知网页尤为有用。 XML 标记名称将与数据存储区的列名尽可能匹配。

使用 `CDynamicAccessor` 方法来获取列信息。 使用此列信息可在运行时动态创建访问器。

列信息存储在由此类创建和管理的缓冲区中。 使用[GetXMLColumnData](#getxmlcolumndata)获取列信息，或使用[GetXMLRowData](#getxmlrowdata)按行获取列数据。

## <a name="example"></a>示例

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor：： GetXMLColumnData

按列将表的列类型信息检索为 XML 格式的字符串数据。

### <a name="syntax"></a>语法

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>parameters

*strOutput*<br/>
弄对包含要检索的列类型信息的字符串缓冲区的引用。 此字符串的格式为与数据存储区的列名称匹配的 XML 标记名称。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

下面说明如何在 XML 中设置列类型信息的格式。 `type` 指定列的数据类型。 请注意，数据类型基于 OLE DB 数据类型，而不是所访问的数据库的类型。

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor：： GetXMLRowData

按行以 XML 格式的字符串数据的形式检索表的全部内容。

### <a name="syntax"></a>语法

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>parameters

*strOutput*<br/>
弄对包含要检索的表数据的缓冲区的引用。 数据的格式为字符串数据，XML 标记名称与数据存储区的列名称相匹配。

*bAppend*<br/>
中一个布尔值，指定是否将字符串追加到输出数据的末尾。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

下面说明如何在 XML 中设置行数据的格式。 以下 `DATA` 表示行数据。 使用 move 方法可移到所需的行。

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)
