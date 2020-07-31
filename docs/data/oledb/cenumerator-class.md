---
title: CEnumerator 类
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: 2a48acb8a961d76c34d2ba85ede5c827c880f400
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214914"
---
# <a name="cenumerator-class"></a>CEnumerator 类

使用 OLE DB 枚举器对象，该对象公开[ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))接口以返回描述所有数据源和枚举器的行集。

## <a name="syntax"></a>语法

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[查找](#find)|搜索可用的提供程序（数据源），查找一个具有指定名称的提供程序。|
|[GetMoniker](#getmoniker)|检索当前记录的 `IMoniker` 接口。|
|[打开](#open)|打开枚举器。|

## <a name="remarks"></a>备注

您可以 `ISourcesRowset` 从此类间接检索数据。

## <a name="cenumeratorfind"></a><a name="find"></a>CEnumerator：： Find

在可用提供程序之间查找指定名称。

### <a name="syntax"></a>语法

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>参数

*szSearchName*<br/>
[in] 要搜索的名称。

### <a name="return-value"></a>返回值

**`true`** 如果找到该名称，则为。 否则为 **`false`** 。

### <a name="remarks"></a>备注

此名称映射到 `SOURCES_NAME` [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))接口的成员。

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>CEnumerator：： GetMoniker

分析显示名称以提取可转换为名字对象的字符串的组件。

### <a name="syntax"></a>语法

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>参数

*ppMoniker*<br/>
弄从当前行的显示名称（[CEnumeratorAccessor：： m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)）分析的名字对象。

*lpszDisplayName*<br/>
中要分析的显示名称。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cenumeratoropen"></a><a name="open"></a>CEnumerator：： Open

绑定枚举器的名字对象（如果已指定），然后通过调用[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85))检索枚举器的行集。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>参数

*pMoniker*<br/>
中指向枚举器的名字对象的指针。

*pClsid*<br/>
中指向枚举器的的指针 `CLSID` 。

*枚举器*<br/>
中对枚举数的引用。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="see-also"></a>另请参阅

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
