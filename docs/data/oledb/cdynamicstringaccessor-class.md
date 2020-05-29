---
title: CDynamicStringAccessor 类
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211857"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 类

使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。

## <a name="syntax"></a>语法

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>要求

**标头**：atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetString](#getstring)|将指定列数据作为字符串检索。|
|[SetString](#setstring)|将指定列数据设置为字符串。|

## <a name="remarks"></a>备注

当[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)请求提供程序报告的本机格式的数据时，`CDynamicStringAccessor` 请求提供程序将从数据存储访问的所有数据作为字符串数据获取。 对于不需要在数据存储中计算值的简单任务（如显示或打印数据存储的内容），这尤其有用。

数据存储中列数据的本机类型并不重要；只要提供程序可支持数据转换，它就将提供字符串格式的数据。 如果提供程序不支持从本机数据类型转换为字符串（不是公共的），则请求调用将返回成功值 DB_S_ERRORSOCCURED，并且相应列的状态将使用 DBSTATUS_E_CANTCONVERTVALUE 指示转换问题。

使用 `CDynamicStringAccessor` 方法来获取列信息。 使用此列信息可在运行时动态创建访问器。

列信息存储在由此类创建和管理的缓冲区中。 使用[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)从缓冲区获取数据，或使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)将数据存储到缓冲区。

有关使用动态访问器类的讨论和示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor：： GetString

将指定列数据作为字符串检索。

### <a name="syntax"></a>语法

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>parameters

*nColumn*<br/>
[in] 列号。 列号从1开始。 值0表示书签列（如果有）。

*pColumnName*<br/>
中指向包含列名称的字符串的指针。

### <a name="return-value"></a>返回值

指向从指定列检索到的字符串值的指针。 此值的类型为 `BaseType`，这将是**CHAR**或**WCHAR** ，具体取决于是否定义了 _UNICODE。 如果找不到指定的列，则返回 NULL。

### <a name="remarks"></a>备注

第二个替代形式采用列名作为 ANSI 字符串。 第三个替代形式采用列名作为 Unicode 字符串。

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor：： SetString

将指定列数据设置为字符串。

### <a name="syntax"></a>语法

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>parameters

*nColumn*<br/>
[in] 列号。 列号从1开始。 特殊值0表示书签列（如果有）。

*pColumnName*<br/>
中指向包含列名称的字符串的指针。

data<br/>
中指向要写入指定列的字符串数据的指针。

### <a name="return-value"></a>返回值

一个指针，指向要将指定列设置为的字符串值。 此值的类型为 `BaseType`，这将是**CHAR**或**WCHAR** ，具体取决于是否定义了 _UNICODE。

### <a name="remarks"></a>备注

第二个替代形式采用列名作为 ANSI 字符串，第三个替代形式采用列名作为 Unicode 字符串。

如果 _SECURE_ATL 定义为具有非零值，则当输入*数据*字符串的长度超过所引用数据列的最大允许长度时，将生成运行时断言失败。 否则，如果输入字符串的长度超过了允许的最大长度，则将被截断。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor 类](../../data/oledb/cxmlaccessor-class.md)
