---
title: CTable 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd9d3b291f967b98017e4136740628ef951ea12a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060125"
---
# <a name="ctable-class"></a>CTable 类

提供了一种方法直接访问简单行集合 （一个不带任何参数）。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>参数

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

请参阅[CCommand](../../data/oledb/ccommand-class.md)有关如何执行命令来访问行集的信息。

## <a name="open"></a> Ctable:: Open

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

#### <a name="parameters"></a>参数

*会话*<br/>
[in]为其打开的表的会话。

*wszTableName*<br/>
[in]若要打开，表的名称传递为 Unicode 字符串。

*szTableName*<br/>
[in]若要打开，表的名称传递为 ANSI 字符串。

*dbid*<br/>
[in]`DBID`要打开的表。

*pPropSet*<br/>
[in]指向数组的指针[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构包含要设置属性和值。 请参阅[属性设置和属性组](/previous-versions/windows/desktop/ms713696)中*OLE DB 程序员参考*Windows SDK 中。 默认值为 NULL 指定任何属性。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构传入*pPropSet*参数。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

有关更多详细信息，请参阅[iopenrowset:: Openrowset](/previous-versions/windows/desktop/ms716724)中*OLE DB 程序员参考*。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)