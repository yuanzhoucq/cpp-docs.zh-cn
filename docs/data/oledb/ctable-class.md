---
title: CTable 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 47c9899889bbbf9b09300779691085786db0e088
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211141"
---
# <a name="ctable-class"></a>CTable 类

提供直接访问简单行集的方法（没有参数的行集）。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>parameters

*TAccessor*<br/>
一个访问器类。

*TRowset*<br/>
行集类。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[打开](#open)|打开表。|

## <a name="remarks"></a>备注

有关如何执行命令以访问行集的信息，请参阅[CCommand](../../data/oledb/ccommand-class.md) 。

## <a name="ctableopen"></a><a name="open"></a>CTable：： Open

打开表。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>parameters

*会议*<br/>
中打开表的会话。

*wszTableName*<br/>
中要打开的表的名称，以 Unicode 字符串形式传递。

*szTableName*<br/>
中要打开的表的名称，以 ANSI 字符串形式传递。

*dbid*<br/>
中要打开的表的 `DBID`。

*传入 ppropset*<br/>
中指向包含要设置的属性和值的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数组的指针。 请参阅 Windows SDK 中*OLE DB 程序员参考*中的[属性集和属性组](/previous-versions/windows/desktop/ms713696(v=vs.85))。 默认值为 NULL，则不指定任何属性。

*ulPropSets*<br/>
中在*传入 ppropset*参数中传递的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数目。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

有关更多详细信息，请参阅*OLE DB 程序员参考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
