---
title: ImplementsHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: d7908670b67df7dbf7b2b74e98f8b59cf30f8e96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184938"
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
指定一个或多个[RuntimeClassType](runtimeclasstype-enumeration.md)枚举器的标志字段。

*ILst*<br/>
接口 Id 的列表。

*IsDelegateToClass*<br/>
**`true`** 如果的当前实例 `Implements` 是*ILst*中第一个接口 ID 的基类，则为; 否则为 **`false`** 。

## <a name="remarks"></a>备注

帮助实现[实现](implements-structure.md)结构。

此模板会遍历接口的列表，并将其添加为基类，以及作为启用所需的信息 `QueryInterface` 。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                    | 描述
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper：： CanCastTo](#cancastto)               | 获取指向指定接口 ID 的指针。
[ImplementsHelper：： CastToUnknown](#casttounknown)       | 获取一个指针，该指针指向 `IUnknown` 当前结构的基础接口 `Implements` 。
[ImplementsHelper：： FillArrayWithIid](#fillarraywithiid) | 将当前第零个模板参数指定的接口 ID 插入指定的数组元素。
[ImplementsHelper：： IidCount](#iidcount)                 | 保留当前对象中已实现的接口 Id 的数量 `Implements` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ImplementsHelper`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper：： CanCastTo

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
对接口 ID 的引用。

*ppv*<br/>
如果此操作成功，则为由*riid*或*iid*指定的接口的指针。

*iid*<br/>
对接口 ID 的引用。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

获取指向指定接口 ID 的指针。

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper：： CastToUnknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

指向基础接口的指针 `IUnknown` 。

### <a name="remarks"></a>备注

获取一个指针，该指针指向 `IUnknown` 当前结构的基础接口 `Implements` 。

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper：： FillArrayWithIid

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>参数

*index*<br/>
从零开始的索引，它指示此操作的起始数组元素。 此操作完成后，*索引*将递增1。

*iid*<br/>
Iid 类型的数组。

### <a name="remarks"></a>备注

将当前第零个模板参数指定的接口 ID 插入指定的数组元素。

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper：： IidCount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>备注

保留当前对象中已实现的接口 Id 的数量 `Implements` 。
