---
title: RuntimeClass 类
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376234"
---
# <a name="runtimeclass-class"></a>RuntimeClass 类

表示继承指定接口并提供指定的 Windows 运行时、经典 COM 和弱引用支持的 WinRT 或 COM 类。

此类提供 WinRT 和 COM 类的样板实现，提供`QueryInterface`的`AddRef`实现`Release`， 等，管理模块的引用计数，并支持为可激活对象提供类工厂。

## <a name="syntax"></a>语法

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>参数

*类标志*<br/>
可选参数。 一个或多个[运行时类类型](runtimeclasstype-enumeration.md)枚举值的组合。 可以`__WRL_CONFIGURATION_LEGACY__`定义宏来更改项目中所有运行时类的 classFlags 的默认值。 如果定义，运行时类实例默认情况下是非敏捷的。 如果未定义运行时类实例，默认情况下是敏捷的。 为了避免歧义，`Microsoft::WRL::FtmBase`请始终指定`TInterfaces``RuntimeClassType::InhibitFtmBase`中的 或 。 请注意，如果使用 InhibitFtmBase 和 FtmBase，则对象将是敏捷的。

*T 接口*<br/>
对象实现超出`IUnknown`的接口列表，`IInspectable`或[由运行时ClassType](runtimeclasstype-enumeration.md)控制的其他接口。 它还可能列出要派生的其他类，特别是`Microsoft::WRL::FtmBase`使对象变得敏捷，并使其实现`IMarshal`。

## <a name="members"></a>成员

`RuntimeClassInitialize`<br/>
一个函数，用于构造对象时`MakeAndInitialize`初始化对象的函数。 如果对象成功初始化，它将返回S_OK;如果初始化失败，则返回 COM 错误代码。 COM 错误代码作为 的返回值传播`MakeAndInitialize`。 请注意，如果使用`RuntimeClassInitialize`模板函数构造对象，`Make`则不调用 该方法。

### <a name="public-constructors"></a>公共构造函数

| 名称                                               | 说明                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [运行时类：运行时类](#runtimeclass)        | 初始化类的`RuntimeClass`当前实例。   |
| [运行时类：：=运行时类](#tilde-runtimeclass) | 取消初始化类的`RuntimeClass`当前实例。 |

### <a name="public-methods"></a>公共方法

| 名称                                                      | 说明                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [运行时类：：添加参考](#addref)                           | 增加当前`RuntimeClass`对象的引用计数。                              |
| [运行时类：:Decrement 参考](#decrementreference)   | 取消当前`RuntimeClass`对象的引用计数。                              |
| [运行时类：：获取 Iid](#getiids)                         | 获取一个数组，该数组可以包含当前`RuntimeClass`对象实现的接口指示。 |
| [运行时类：：获取运行时类名称](#getruntimeclassname) | 获取当前`RuntimeClass`对象的运行时类名称。                                  |
| [运行时类：：获取信任级别](#gettrustlevel)             | 获取当前`RuntimeClass`对象的信任级别。                                         |
| [运行时类：：获取 Weak 引用](#getweakreference)       | 获取指向当前`RuntimeClass`对象的弱引用对象的指针。                 |
| [运行时类：：内部AddRef](#internaladdref)           | 将引用计数递增到当前`RuntimeClass`对象。                               |
| [运行时类：：查询接口](#queryinterface)           | 检索指向指定接口 ID 的指针。                                                 |
| [运行时类：：发布](#release)                         | 对当前`RuntimeClass`对象执行 COM 释放操作。                             |

## <a name="inheritance-hierarchy"></a>继承层次结构

这是实现详细信息。

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>运行时类：：=运行时类

取消初始化类的`RuntimeClass`当前实例。

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>运行时类：：添加参考

增加当前`RuntimeClass`对象的引用计数。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>运行时类：:Decrement 参考

取消当前`RuntimeClass`对象的引用计数。

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>运行时类：：获取 Iid

获取一个数组，该数组可以包含当前`RuntimeClass`对象实现的接口指示。

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>参数

*iidCount*<br/>
此操作完成后，数组*iid*中的元素总数。

*伊德*<br/>
此操作完成后，指向接口 ID 数组的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_OUTOFMEMORY。

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>运行时类：：获取运行时类名称

获取当前`RuntimeClass`对象的运行时类名称。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>参数

*运行时名称*<br/>
此操作完成后，运行时类名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`未定义，将发出断言错误。

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>运行时类：：获取信任级别

获取当前`RuntimeClass`对象的信任级别。

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>参数

*信任吕尔*<br/>
此操作完成后，当前`RuntimeClass`对象的信任级别。

### <a name="return-value"></a>返回值

始终 S_OK。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`未定义，将发出断言错误。

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>运行时类：：获取 Weak 引用

获取指向当前`RuntimeClass`对象的弱引用对象的指针。

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>参数

*弱参考*<br/>
此操作完成后，指向弱引用对象的指针。

### <a name="return-value"></a>返回值

始终 S_OK。

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>运行时类：：内部AddRef

将引用计数递增到当前`RuntimeClass`对象。

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>返回值

生成的引用计数。

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>运行时类：：查询接口

检索指向指定接口 ID 的指针。

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppvObject*<br/>
完成此操作后，指向*riid*参数指定的接口的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="runtimeclassrelease"></a><a name="release"></a>运行时类：：发布

对当前`RuntimeClass`对象执行 COM 释放操作。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果引用计数变为零，则`RuntimeClass`删除该对象。

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>运行时类：运行时类

初始化类的`RuntimeClass`当前实例。

```cpp
RuntimeClass();
```
