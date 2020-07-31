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
ms.openlocfilehash: 9fb911b469497a007550c042ade97b5a463e78fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220439"
---
# <a name="crestrictions-class"></a>CRestrictions 类

允许你指定架构行集的限制的泛型类。

## <a name="syntax"></a>语法

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>参数

*T*<br/>
用于访问器的类。

*nRestrictions*<br/>
架构行集的限制列数。

*pguid*<br/>
指向架构的 GUID 的指针。

## <a name="requirements"></a>要求

**标头：** atldbsch。h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[打开](#open)|根据用户提供的限制返回结果集。|

## <a name="crestrictionsopen"></a><a name="open"></a>CRestrictions：： Open

根据用户提供的限制返回结果集。

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

*会议*<br/>
中指定用于连接到数据源的现有会话对象。

*lpszParam*<br/>
中指定架构行集的限制。

*bBind*<br/>
中指定是否自动绑定列映射。 默认值为 **`true`** ，这将导致自动绑定列映射。 将*bBind*设置为可 **`false`** 阻止自动绑定列映射，以便可以手动绑定。 （手动绑定对 OLAP 用户特别感兴趣。）

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

最多可在架构行集中指定7个限制。

有关每个架构行集的定义限制的信息，请参阅[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
