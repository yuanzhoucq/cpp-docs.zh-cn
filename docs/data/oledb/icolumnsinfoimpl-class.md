---
title: IColumnsInfoImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 802c105e7795cdce604e72983f4fda549abcd5fb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418264"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl 类

提供的实现[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))接口。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo, 
   public CDBIDOps
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IColumnsInfoImpl`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|返回所需的大多数使用者的列元数据。|
|[MapColumnIDs](#mapcolumnids)|在由指定的列 Id 标识的行集返回的列序号的数组。|

## <a name="remarks"></a>备注

针对行集和命令必需的接口。 若要修改的提供程序的行为`IColumnsInfo`实现中，您需要修改提供程序列映射。

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo

返回所需的大多数使用者的列元数据。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>参数

请参阅[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程序员参考*。

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

在由指定的列 Id 标识的行集返回的列序号的数组。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>参数

请参阅[IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85))中*OLE DB 程序员参考*。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)