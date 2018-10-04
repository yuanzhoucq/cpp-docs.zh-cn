---
title: ImplementsHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 574d0dbf6a252f65dd6c15681a243ce0e4086f0e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788495"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>参数

*RuntimeClassFlagsT*<br/>
指定一个或多个标记的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。

*ILst*<br/>
接口 Id 的列表。

*IsDelegateToClass*<br/>
指定`true`如果当前实例`Implements`是一个基类中的第一个接口 ID *ILst*; 否则为`false`。

## <a name="remarks"></a>备注

可帮助实现[实现](../windows/implements-structure.md)结构。

此模板会遍历接口的列表，并将其添加作为基类，这些类，以及启用所需的信息`QueryInterface`。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                    | 描述
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Implementshelper:: Cancastto](#cancastto)               | 获取一个指针指向指定的接口 id。
[Implementshelper:: Casttounknown](#casttounknown)       | 获取一个指针指向的基础`IUnknown`当前接口`Implements`结构。
[Implementshelper:: Fillarraywithiid](#fillarraywithiid) | 将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。
[Implementshelper:: Iidcount](#iidcount)                 | 存储在当前实现的接口 Id 的数目`Implements`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ImplementsHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>Implementshelper:: Cancastto

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
引用接口 id。

*ppv*<br/>
如果此操作成功，通过指定指向接口的指针*riid*或*iid*。

*iid*<br/>
引用接口 id。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

获取一个指针指向指定的接口 id。

## <a name="casttounknown"></a>Implementshelper:: Casttounknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

对基础指针`IUnknown`接口。

### <a name="remarks"></a>备注

获取一个指针指向的基础`IUnknown`当前接口`Implements`结构。

## <a name="fillarraywithiid"></a>Implementshelper:: Fillarraywithiid

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>参数

*index*<br/>
一个从零开始的索引，该值指示此操作的起始数组元素。 此操作完成后，*索引*都会增加 1。

*iid*<br/>
类型 Iid 的数组。

### <a name="remarks"></a>备注

将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。

## <a name="iidcount"></a>Implementshelper:: Iidcount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>备注

存储在当前实现的接口 Id 的数目`Implements`对象。
