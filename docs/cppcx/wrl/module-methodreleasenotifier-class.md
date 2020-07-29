---
title: Module::MethodReleaseNotifier 类
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 5b0e5766fda878acb1fdc54a79ce162444eb06de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225717"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 类

在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由对象及其指向方法的指针成员指定。

## <a name="syntax"></a>语法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>参数

*T*<br/>
其成员函数为事件处理程序的对象的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                                                 | 说明
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | 初始化 `Module::MethodReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

“属性”                                                                   | 说明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： Invoke](#methodreleasenotifier-invoke) | 调用与当前对象关联的事件处理程序 `Module::MethodReleaseNotifier` 。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                                                    | 说明
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： method_](#methodreleasenotifier-method) | 保存指向当前对象的事件处理程序的指针 `Module::MethodReleaseNotifier` 。
[Module：： MethodReleaseNotifier：： object_](#methodreleasenotifier-object) | 保存一个指向对象的指针，该对象的成员函数是当前对象的事件处理程序 `Module::MethodReleaseNotifier` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module：： MethodReleaseNotifier：： Invoke

调用与当前对象关联的事件处理程序 `Module::MethodReleaseNotifier` 。

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module：： MethodReleaseNotifier：： method_

保存指向当前对象的事件处理程序的指针 `Module::MethodReleaseNotifier` 。

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module：： MethodReleaseNotifier：： MethodReleaseNotifier

初始化 `Module::MethodReleaseNotifier` 类的新实例。

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>参数

*object*<br/>
一个对象，其成员函数为事件处理程序。

*method*<br/>
作为事件处理程序的参数*对象*的成员函数。

*拆卸*<br/>
指定 **`true`** 以启用对基础[模块：： ReleaseNotifier：： Release （）](module-releasenotifier-class.md#releasenotifier-release)方法的调用; 否则指定 **`false`** 。

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module：： MethodReleaseNotifier：： object_

保存一个指向对象的指针，该对象的成员函数是当前对象的事件处理程序 `Module::MethodReleaseNotifier` 。

```cpp
T* object_;
```
