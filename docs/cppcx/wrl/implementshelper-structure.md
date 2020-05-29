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
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371400"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>参数

*运行时类标志T*<br/>
指定一个或多个[运行时类类型](runtimeclasstype-enumeration.md)枚举器的标志字段。

*ILst*<br/>
接口指示列表。

*是委托类*<br/>
如果 当前`Implements`实例是*ILst*中第一个接口 ID 的基类，请**指定 true;** 否则，**假**。

## <a name="remarks"></a>备注

帮助实现[实现器](implements-structure.md)结构。

此模板遍历接口列表，并将它们添加为基类，并作为启用`QueryInterface`所需的信息。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                    | 说明
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[实现帮助器：：坎卡斯特托](#cancastto)               | 获取指向指定接口 ID 的指针。
[实现帮助器：：Castto 未知](#casttounknown)       | 获取指向当前`IUnknown``Implements`结构的基础接口的指针。
[实现帮助器：：fillarray 与 Id](#fillarraywithiid) | 将当前零点模板参数指定的接口 ID 插入指定的数组元素。
[实现帮助器：：IidCount](#iidcount)                 | 保存当前`Implements`对象中已实现的接口指示数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ImplementsHelper`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>实现帮助器：：坎卡斯特托

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

*Ppv*<br/>
如果此操作成功，则指向*riid*或*iid*指定的接口的指针。

*Iid*<br/>
对接口 ID 的引用。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

获取指向指定接口 ID 的指针。

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>实现帮助器：：Castto 未知

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

指向基础`IUnknown`接口的指针。

### <a name="remarks"></a>备注

获取指向当前`IUnknown``Implements`结构的基础接口的指针。

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>实现帮助器：：fillarray 与 Id

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>参数

*index*<br/>
一个基于零的索引，指示此操作的起始数组元素。 此操作完成后，*索引*将递增 1。

*伊德*<br/>
IID 类型的数组。

### <a name="remarks"></a>备注

将当前零点模板参数指定的接口 ID 插入指定的数组元素。

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>实现帮助器：：IidCount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>备注

保存当前`Implements`对象中已实现的接口指示数。
