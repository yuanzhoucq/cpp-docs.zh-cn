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
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371306"
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
[模块：：通用释放程序：：通用释放程序](#genericreleasenotifier-genericreleasenotifier) | 初始化 `Module::GenericReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                                     | 说明
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[模块：：通用释放程序：：调用](#genericreleasenotifier-invoke) | 调用与当前`Module::GenericReleaseNotifier`对象关联的事件处理程序。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                                                          | 说明
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[模块：：通用释放程序：：callback_](#genericreleasenotifier-callback) | 保存与当前`Module::GenericReleaseNotifier`对象关联的 lambda、functor 或指向函数的指针事件处理程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>模块：：通用释放程序：：callback_

保存与当前`Module::GenericReleaseNotifier`对象关联的 lambda、functor 或指向函数的指针事件处理程序。

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>模块：：通用释放程序：：通用释放程序

初始化 `Module::GenericReleaseNotifier` 类的新实例。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>参数

*回调 (callback)*<br/>
可以使用括号函数运算符 （）`()`调用的 lambda、functor 或指针到函数事件处理程序。

*释放*<br/>
指定`true`以启用调用基础[模块：：释放说明器：：：释放（）](module-releasenotifier-class.md#releasenotifier-release)方法;否则，指定`false`。

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>模块：：通用释放程序：：调用

调用与当前`Module::GenericReleaseNotifier`对象关联的事件处理程序。

```cpp
void Invoke();
```
