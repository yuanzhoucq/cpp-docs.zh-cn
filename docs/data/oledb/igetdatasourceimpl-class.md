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
ms.openlocfilehash: cd6b56f4281a2fdde77229ec54be6d6289a87148
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556564"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 类

提供的实现[IGetDataSource](https://docs.microsoft.com/previous-versions/windows/desktop/ms709721(v=vs.85))对象。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IGetDataSourceImpl`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetDataSource](#getdatasource)|在创建会话的数据源对象上返回的接口指针。|

## <a name="remarks"></a>备注

用于获取数据源对象的接口指针的会话，这是必需的接口。

## <a name="getdatasource"></a> Igetdatasourceimpl:: Getdatasource

在创建会话的数据源对象上返回的接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>参数

请参阅[IGetDataSource::GetDataSource](https://docs.microsoft.com/previous-versions/windows/desktop/ms725443(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

如果你需要访问数据源对象中的属性，这很有用。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)