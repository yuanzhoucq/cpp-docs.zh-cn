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
ms.openlocfilehash: 7437f4e1f6874d4c708780a146e1761ac6d98305
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225730"
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

名称                                                                                                     | 说明
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | 初始化 `Module::GenericReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

“属性”                                                                     | 说明
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： Invoke](#genericreleasenotifier-invoke) | 调用与当前对象关联的事件处理程序 `Module::GenericReleaseNotifier` 。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                                                          | 说明
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： callback_](#genericreleasenotifier-callback) | 保存与当前对象相关联的 lambda、函子或指向函数的指针事件处理程序 `Module::GenericReleaseNotifier` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Module：： GenericReleaseNotifier：： callback_

保存与当前对象相关联的 lambda、函子或指向函数的指针事件处理程序 `Module::GenericReleaseNotifier` 。

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Module：： GenericReleaseNotifier：： GenericReleaseNotifier

初始化 `Module::GenericReleaseNotifier` 类的新实例。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>参数

*拨*<br/>
一个 lambda、函子或指向函数的事件处理程序，可使用括号函数运算符（）进行调用 `()` 。

*拆卸*<br/>
指定 **`true`** 以启用对基础[模块：： ReleaseNotifier：： Release （）](module-releasenotifier-class.md#releasenotifier-release)方法的调用; 否则指定 **`false`** 。

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Module：： GenericReleaseNotifier：： Invoke

调用与当前对象关联的事件处理程序 `Module::GenericReleaseNotifier` 。

```cpp
void Invoke();
```
