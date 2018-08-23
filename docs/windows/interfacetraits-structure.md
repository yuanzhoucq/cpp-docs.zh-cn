---
title: InterfaceTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 966759acdac3cf78625cfd072471245a6e42ad63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597110"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<
   typename I0
>
struct __declspec(novtable) InterfaceTraits;
template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>参数

*I0*  
接口的名称。

*CloakedType*  
有关`RuntimeClass`，`Implements`和`ChainInterfaces`，不会在列表中的接口支持接口 Id。

## <a name="remarks"></a>备注

实现的接口的共同特征。

第二个模板是掩蔽的接口的专用化。 第三个模板是为 Nil 参数专用化。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`Base`|同义词*I0*模板参数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指示是否指定的指针可以转换为一个指向`Base`。|
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|将转换为指针指定的指针`Base`。|
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|将转换为指针指定的指针`IUnknown`。|
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|为指定的接口 ID`Base`索引参数指定的数组元素。|
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|验证`Base`正确派生。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[InterfaceTraits::IidCount 常量](../windows/interfacetraits-iidcount-constant.md)|保存数量的接口 Id 与当前相关联**InterfaceTraits**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceTraits`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)