---
title: ClassFactory 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372669"
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
第零个接口。

*I1*<br/>
第一个接口。

*I2*<br/>
第二个接口。

## <a name="remarks"></a>备注

利用`ClassFactory`来提供用户定义的工厂实现。

以下编程模式演示如何使用[实现器](implements-structure.md)结构在类工厂上指定三个多个接口。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                        | 说明
------------------------------------------- | -----------
[类工厂：：类工厂](#classfactory) |

### <a name="public-methods"></a>公共方法

名称                                            | 说明
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[类工厂：：添加参考](#addref)                 | 增加当前`ClassFactory`对象的引用计数。
[类工厂：：锁服务器](#lockserver)         | 增加或递减当前`ClassFactory`对象跟踪的基础对象数。
[类工厂：：查询接口](#queryinterface) | 检索指向参数指定的接口的指针。
[类工厂：：发布](#release)               | 取消当前`ClassFactory`对象的引用计数。

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

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>类工厂：：添加参考

增加当前`ClassFactory`对象的引用计数。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>类工厂：：类工厂

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>类工厂：：锁服务器

增加或递减当前`ClassFactory`对象跟踪的基础对象数。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>参数

*羊群*<br/>
**true**以增加跟踪对象的数量。 **false**以减少被跟踪对象的数量。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_FAIL。

### <a name="remarks"></a>备注

`ClassFactory`跟踪[模块](module-class.md)类的基础实例中的对象。

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>类工厂：：查询接口

检索指向参数指定的接口的指针。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppvObject*<br/>
此操作完成后，指向参数*riid*指定的接口的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="classfactoryrelease"></a><a name="release"></a>类工厂：：发布

取消当前`ClassFactory`对象的引用计数。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。
