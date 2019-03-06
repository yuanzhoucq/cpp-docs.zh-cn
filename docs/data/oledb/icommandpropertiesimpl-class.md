---
title: ICommandPropertiesImpl 类
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: b9d6c9aab2b12859462abfa2a842754128e72306
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416652"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 类

提供的实现[ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85))接口。

## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自

*PropClass*<br/>
属性类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetProperties](#getproperties)|返回在当前请求的行集的行集属性组中的属性列表。|
|[SetProperties](#setproperties)|行集属性组中设置属性。|

## <a name="remarks"></a>备注

这是必需的对于命令。 通过定义一个静态函数提供了该实现[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)宏。

## <a name="getproperties"></a> Icommandpropertiesimpl:: Getproperties

返回使用该命令的属性映射的所有请求的属性集。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>参数

请参阅[icommandproperties:: Getproperties](/previous-versions/windows/desktop/ms723119(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

请参阅 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

## <a name="setproperties"></a> Icommandpropertiesimpl:: Setproperties

设置命令对象的属性。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>参数

请参阅[icommandproperties:: Setproperties](/previous-versions/windows/desktop/ms711497(v=vs.85))中*OLE DB 程序员参考*。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)