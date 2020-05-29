---
title: IRowsetIdentityImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 20f558099c02d7de8a20b3cf631812b44a742a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210400"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 类

实现 OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))接口，该接口启用行标识测试。

## <a name="syntax"></a>语法

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetIdentityImpl`的类。

*RowClass*<br/>
`HROW`的存储单元。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[IsSameRow](#issamerow)|比较两个行句柄，以确定它们是否引用相同的行。|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a>IRowsetIdentityImpl：： IsSameRow

比较两个行句柄，以确定它们是否引用相同的行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetIdentity：： IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) 。

### <a name="remarks"></a>备注

为了比较行句柄，此方法会将 `HROW` 句柄强制转换为 `RowClass` 成员，并对指针调用 `memcmp`。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
