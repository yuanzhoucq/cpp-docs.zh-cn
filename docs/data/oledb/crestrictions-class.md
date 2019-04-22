---
title: CRestrictions 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 309bb7e707d649cf78528f3d0df6cf8e43201823
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040614"
---
# <a name="crestrictions-class"></a>CRestrictions 类

泛型类，可用于指定架构行集的限制。

## <a name="syntax"></a>语法

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>参数

*T*<br/>
取值函数使用的类。

*nRestrictions*<br/>
架构行集的限制列数。

*pguid*<br/>
指向架构的 GUID 的指针。

## <a name="requirements"></a>要求

**标头：** atldbsch.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[打开](#open)|返回一个结果集，根据用户提供的限制。|

## <a name="open"></a> CRestrictions::Open

返回一个结果集，根据用户提供的限制。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>参数

*session*<br/>
[in]指定用于连接到数据源的现有会话对象。

*lpszParam*<br/>
[in]架构行集上指定的限制。

*bBind*<br/>
[in]指定是否自动绑定列映射。 默认值是 **，则返回 true**，这将导致自动绑定的列映射。 设置*bBind*到**false**可防止自动绑定列映射，以便您可以手动绑定。 （手动绑定是 OLAP 用户特别关注。）

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

架构行集上，可以指定最多七个限制。

请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))有关每个架构行集上定义的限制信息。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)