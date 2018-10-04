---
title: ClassFactory 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e3639bb9d6ca88862b3a2fb4367fc429a665287
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788664"
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
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>参数

*I0*<br/>
第零个接口中。

*I1*<br/>
第一个接口。

*I2*<br/>
第二个接口。

## <a name="remarks"></a>备注

利用`ClassFactory`能够提供的用户定义的工厂实现。

下面的编程模式演示如何使用[实现](../windows/implements-structure.md)结构，以在一个类工厂上指定三个以上的接口。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                        | 描述
------------------------------------------- | -----------
[Classfactory:: Classfactory](#classfactory) |

### <a name="public-methods"></a>公共方法

名称                                            | 描述
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[Classfactory:: Addref](#addref)                 | 递增当前引用计数`ClassFactory`对象。
[Classfactory:: Lockserver](#lockserver)         | 增加或减少基础对象数量跟踪的当前`ClassFactory`对象。
[Classfactory:: Queryinterface](#queryinterface) | 检索指向指定参数的接口的指针。
[Classfactory:: Release](#release)               | 递减引用计数当前`ClassFactory`对象。

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

## <a name="addref"></a>Classfactory:: Addref

递增当前引用计数`ClassFactory`对象。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="classfactory"></a>Classfactory:: Classfactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>Classfactory:: Lockserver

增加或减少基础对象数量跟踪的当前`ClassFactory`对象。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>参数

*纷纷采用*<br/>
若要递增跟踪对象的数量，则为 `true`。 若要递减跟踪对象的数量，则为 `false`。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_FAIL。

### <a name="remarks"></a>备注

`ClassFactory` 跟踪的基础实例中的对象[模块](../windows/module-class.md)类。

## <a name="queryinterface"></a>Classfactory:: Queryinterface

检索指向指定参数的接口的指针。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppvObject*<br/>
此操作完成后，指向由参数指定的接口的指针*riid*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="release"></a>Classfactory:: Release

递减引用计数当前`ClassFactory`对象。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。
