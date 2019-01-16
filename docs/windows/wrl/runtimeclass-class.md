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
ms.openlocfilehash: d45fe7c6d794f216da93ffbd95dbb7058d3336f3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335755"
---
# <a name="runtimeclass-class"></a>RuntimeClass 类

表示一个 WinRT 或 COM 类，继承的指定的接口并提供指定的 Windows 运行时、 经典 COM 和弱引用支持。

此类提供了 WinRT 和 COM 类，提供的实现的样板实现`QueryInterface`， `AddRef`，`Release`等，管理模块的引用计数和提供的类工厂的支持可激活的对象。

## <a name="syntax"></a>语法

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>参数

*classFlags*<br/>
可选参数。 一个或多个组合[RuntimeClassType](runtimeclasstype-enumeration.md)枚举值。 `__WRL_CONFIGURATION_LEGACY__`可以定义宏，若要更改的项目中的所有运行时类 classFlags 的默认值。 如果定义，RuntimeClass 实例是默认情况下非敏捷。 未定义时，RuntimeClass 实例是默认情况下敏捷的。 若要避免多义性始终指定`Microsoft::WRL::FtmBase`中`TInterfaces`或`RuntimeClassType::InhibitFtmBase`。 请注意，如果 InhibitFtmBase 和 FtmBase 是同时使用该对象将是敏捷类。

*TInterfaces*<br/>
接口列表中的该对象实现之外`IUnknown`，`IInspectable`或控制的其他接口[RuntimeClassType](runtimeclasstype-enumeration.md)。 它还可能会列出其他类以值得注意的是派生自`Microsoft::WRL::FtmBase`使对象敏捷，从而使该实现`IMarshal`。

## <a name="members"></a>成员

`RuntimeClassInitialize`<br/>
如果初始化该对象的函数的`MakeAndInitialize`模板函数用于构造对象。 如果初始化失败，则返回如果对象已成功初始化，则为 S_OK 或 COM 错误代码。 COM 错误代码传播的返回值作为`MakeAndInitialize`。 请注意，`RuntimeClassInitialize`如果不调用方法`Make`模板函数用于构造对象。

### <a name="public-constructors"></a>公共构造函数

| 名称                                               | 描述                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | 初始化当前实例的`RuntimeClass`类。   |
| [RuntimeClass::~RuntimeClass](#tilde-runtimeclass) | 取消初始化的当前实例`RuntimeClass`类。 |

### <a name="public-methods"></a>公共方法

| 名称                                                      | 描述                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | 递增当前引用计数`RuntimeClass`对象。                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | 递减引用计数当前`RuntimeClass`对象。                              |
| [RuntimeClass::GetIids](#getiids)                         | 获取一个数组，其中可以包含的接口 Id 由当前实现`RuntimeClass`对象。 |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | 获取当前的运行时类名称`RuntimeClass`对象。                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | 获取当前的信任级别`RuntimeClass`对象。                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | 获取一个指向弱引用对象的当前`RuntimeClass`对象。                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | 递增到当前的引用计数`RuntimeClass`对象。                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | 检索指向指定的接口 id。                                                 |
| [RuntimeClass::Release](#release)                         | 执行 COM 释放操作对当前`RuntimeClass`对象。                             |

## <a name="inheritance-hierarchy"></a>继承层次结构

这是实现详细信息。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="tilde-runtimeclass"></a>RuntimeClass:: ~ RuntimeClass

取消初始化的当前实例`RuntimeClass`类。

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>RuntimeClass::AddRef

递增当前引用计数`RuntimeClass`对象。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="decrementreference"></a>RuntimeClass::DecrementReference

递减引用计数当前`RuntimeClass`对象。

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="getiids"></a>RuntimeClass::GetIids

获取一个数组，其中可以包含的接口 Id 由当前实现`RuntimeClass`对象。

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>参数

*iidCount*<br/>
此操作完成后，数组中的元素总数*iid*。

*iids*<br/>
此操作完成后，指向接口 ID 数组的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_OUTOFMEMORY。

## <a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

获取当前的运行时类名称`RuntimeClass`对象。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>参数

*runtimeName*<br/>
此操作完成后，运行时类名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果发出断言错误`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`并不定义。

## <a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

获取当前的信任级别`RuntimeClass`对象。

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>参数

*trustLvl*<br/>
此操作完成后，当前的信任级别`RuntimeClass`对象。

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

如果发出断言错误`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`并不定义。

## <a name="getweakreference"></a>RuntimeClass::GetWeakReference

获取一个指向弱引用对象的当前`RuntimeClass`对象。

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>参数

*weakReference*<br/>
此操作完成后，指向弱引用对象的指针。

### <a name="return-value"></a>返回值

始终返回 S_OK。

## <a name="internaladdref"></a>RuntimeClass::InternalAddRef

递增到当前的引用计数`RuntimeClass`对象。

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>返回值

在生成的引用计数。

## <a name="queryinterface"></a>RuntimeClass::QueryInterface

检索指向指定的接口 id。

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
当此 opereation 完成时，为指定的接口指针*riid*参数。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="release"></a>RuntimeClass::Release

执行 COM 释放操作对当前`RuntimeClass`对象。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果引用计数变为零，`RuntimeClass`删除对象。

## <a name="runtimeclass"></a>RuntimeClass::RuntimeClass

初始化当前实例的`RuntimeClass`类。

```cpp
RuntimeClass();
```
