---
title: Module::GenericReleaseNotifier 类
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: 318415c9726426cbd60c205759a6ff8572cc555e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335552"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 类

在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由 lambda、functor 或 pointer-to-function 指定。

## <a name="syntax"></a>语法

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>参数

*T*<br/>
包含事件处理程序位置的数据成员的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                                                     | 描述
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | 初始化 `Module::GenericReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                                     | 描述
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::Invoke](#genericreleasenotifier-invoke) | 调用与当前关联的事件处理程序`Module::GenericReleaseNotifier`对象。

### <a name="protected-data-members"></a>受保护的数据成员

name                                                                          | 描述
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | 包含 lambda、 functor 或与当前关联的指针函数事件处理程序`Module::GenericReleaseNotifier`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft:: wrl

## <a name="genericreleasenotifier-callback"></a>Module::GenericReleaseNotifier::callback_

包含 lambda、 functor 或与当前关联的指针函数事件处理程序`Module::GenericReleaseNotifier`对象。

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier

初始化 `Module::GenericReleaseNotifier` 类的新实例。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>参数

*callback*<br/>
Lambda、 functor 或可以使用括号函数运算符调用的函数指针事件处理程序 (`()`)。

*release*<br/>
指定`true`若要启用调用基础[模块:: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release)方法; 否则，请指定`false`。

## <a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier::Invoke

调用与当前关联的事件处理程序`Module::GenericReleaseNotifier`对象。

```cpp
void Invoke();
```
