---
title: CEnumeratorAccessor 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: d85f630a01ab7e2a07035a8a304a56be91eca8a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545629"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor 类

由[CEnumerator](../../data/oledb/cenumerator-class.md)用来访问枚举器行集中的数据。

## <a name="syntax"></a>语法

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_bIsParent](#bisparent)|一个变量，该变量指示枚举器是否为父枚举器（如果行是枚举器）。|
|[m_nType](#ntype)|一个变量，该变量指示行是否描述数据源或枚举器。|
|[m_szDescription](#szdescription)|数据源或枚举器的说明。|
|[m_szName](#szname)|数据源或枚举器的名称。|
|[m_szParseName](#szparsename)|要传递给[IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname)以获取数据源或枚举器的名字对象的字符串。|

## <a name="remarks"></a>备注

此行集包含当前枚举器中可见的数据源和枚举器。

## <a name="cenumeratoraccessorm_bisparent"></a><a name="bisparent"></a>CEnumeratorAccessor：： m_bIsParent

一个变量，该变量指示枚举器是否为父枚举器（如果行是枚举器）。

### <a name="syntax"></a>语法

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_ntype"></a><a name="ntype"></a>CEnumeratorAccessor：： m_nType

一个变量，该变量指示行是否描述数据源或枚举器。

### <a name="syntax"></a>语法

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szdescription"></a><a name="szdescription"></a>CEnumeratorAccessor：： m_szDescription

数据源或枚举器的说明。

### <a name="syntax"></a>语法

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szname"></a><a name="szname"></a>CEnumeratorAccessor：： m_szName

数据源或枚举器的名称。

### <a name="syntax"></a>语法

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szparsename"></a><a name="szparsename"></a>CEnumeratorAccessor：： m_szParseName

要传递给[IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname)以获取数据源或枚举器的名字对象的字符串。

### <a name="syntax"></a>语法

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>备注

有关详细信息，请参阅*OLE DB 程序员参考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)