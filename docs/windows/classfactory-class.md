---
title: ClassFactory 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f033fc20fac656e6b9fcfa9ac822099ea929d62
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611800"
---
# <a name="classfactory-class"></a>ClassFactory 类

实现 `IClassFactory` 接口的基本功能。

## <a name="syntax"></a>语法

```cpp
template <
   typename I0 = Details::Nil,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil
>
class ClassFactory : public Details::RuntimeClass<
   typename Details::InterfaceListHelper<IClassFactory,
   I0,
   I1,
   I2,
   Details::Nil>::TypeT,
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
      false>;
```

### <a name="parameters"></a>参数

*I0*  
第零个接口中。

*I1*  
第一个接口。

*I2*  
第二个接口。

## <a name="remarks"></a>备注

利用**ClassFactory**能够提供的用户定义的工厂实现。

下面的编程模式演示如何使用[实现](../windows/implements-structure.md)结构，以在一个类工厂上指定三个以上的接口。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[ClassFactory::ClassFactory 构造函数](../windows/classfactory-classfactory-constructor.md)||

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|当前的引用计数递增**ClassFactory**对象。|
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|增加或减少基础对象数量跟踪的当前**ClassFactory**对象。|
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|检索指向指定参数的接口的指针。|
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|递减引用计数的当前**ClassFactory**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)  
[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)