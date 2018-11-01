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
ms.openlocfilehash: ff72d672db963a166284c9ea0f7e3e8c1a89d5e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594709"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor 类

可以在不知道数据存储区的架构 （基础结构） 时，作为字符串数据访问数据源。

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
|[GetXMLRowData](#getxmlrowdata)|按行中检索表的全部内容。|

## <a name="remarks"></a>备注

但是，`CXMLAccessor`不同于`CDynamicStringAccessorW`，因为它会将转换从数据存储为 XML 格式 （标记） 的数据访问的所有数据。 这是非常适合 XML 感知的 Web 页面的输出。 XML 标记名称将尽可能接近地匹配数据存储区的列名称。

使用`CDynamicAccessor`方法可获取列信息。 此列信息用于在运行时动态创建取值函数。

创建和管理此类缓冲区中存储的列信息。 获取列信息使用[GetXMLColumnData](#getxmlcolumndata)或按行使用获取列数据[GetXMLRowData](#getxmlrowdata)。

## <a name="example"></a>示例

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> Cxmlaccessor:: Getxmlcolumndata

按列检索为 XML 格式的字符串数据的列类型信息的表。

### <a name="syntax"></a>语法

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>参数

*strOutput*<br/>
[out]对包含要检索的列类型信息的字符串缓冲区的引用。 使用与数据存储区的列名称匹配的 XML 标记名称格式化的字符串。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

下面显示了如何在 XML 中设置列类型信息的格式。 `type` 指定列的数据类型。 请注意，将数据类型基于 OLE DB 数据类型，不是那些正在访问的数据库。

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> Cxmlaccessor:: Getxmlrowdata

检索表的整个内容为 XML 格式的字符串数据，按行。

### <a name="syntax"></a>语法

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput, 
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>参数

*strOutput*<br/>
[out]对包含要检索的表数据的缓冲区的引用。 数据格式化为使用与数据存储区的列名称匹配的 XML 标记名称的字符串数据。

*bAppend*<br/>
[in]一个布尔值，指定是否要将字符串追加到输出数据的末尾。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

下面显示了如何在 XML 中设置行数据的格式。 `DATA` 下面表示行数据。 使用 move 方法移动到所需的一行。

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)