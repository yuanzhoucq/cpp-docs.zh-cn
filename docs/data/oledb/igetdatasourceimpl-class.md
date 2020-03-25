---
title: IGetDataSourceImpl 类
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 596dd2ea7f65040ae526662974d210c1f99a0cf2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210608"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 类

提供[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))对象的实现。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IGetDataSourceImpl`的类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetDataSource](#getdatasource)|返回创建会话的数据源对象上的接口指针。|

## <a name="remarks"></a>备注

这是会话的必需接口，用于获取指向数据源对象的接口指针。

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a>IGetDataSourceImpl：： GetDataSource

返回创建会话的数据源对象上的接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IGetDataSource：： GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) 。

### <a name="remarks"></a>备注

如果需要访问数据源对象中的属性，则此方法很有用。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
