---
title: IRowsetIdentityImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: b70ebdaa44331d9fa545763f0dd19e6320dd652b
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556213"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 类

实现 OLE DB [IRowsetIdentity](https://docs.microsoft.com/previous-versions/windows/desktop/ms715913(v=vs.85))接口，可对行标识进行测试。

## <a name="syntax"></a>语法

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>参数

*T*<br/>
一个类派生自`IRowsetIdentityImpl`。

*RowClass*<br/>
为存储单元`HROW`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[IsSameRow](#issamerow)|比较两个行句柄，以了解它们是否引用同一行。|

## <a name="issamerow"></a> Irowsetidentityimpl:: Issamerow

比较两个行句柄，以了解它们是否引用同一行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetIdentity::IsSameRow](https://docs.microsoft.com/previous-versions/windows/desktop/ms719629(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

若要比较的行句柄，此方法强制转换`HROW`句柄`RowClass`成员和调用`memcmp`指针。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)