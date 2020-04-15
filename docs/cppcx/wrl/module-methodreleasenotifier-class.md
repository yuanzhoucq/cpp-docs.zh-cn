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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371290"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 类

在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由对象及其指向方法的成员指定。

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
[模块：：方法释放程序：：方法释放器](#methodreleasenotifier-methodreleasenotifier) | 初始化 `Module::MethodReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                                   | 说明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[模块：：方法释放程序：：调用](#methodreleasenotifier-invoke) | 调用与当前`Module::MethodReleaseNotifier`对象关联的事件处理程序。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                                                    | 说明
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[模块：：方法释放程序：：method_](#methodreleasenotifier-method) | 为当前`Module::MethodReleaseNotifier`对象保留指向事件处理程序的指针。
[模块：：方法释放程序：：object_](#methodreleasenotifier-object) | 保存指向其成员函数是当前`Module::MethodReleaseNotifier`对象的事件处理程序的对象的指针。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>模块：：方法释放程序：：调用

调用与当前`Module::MethodReleaseNotifier`对象关联的事件处理程序。

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>模块：：方法释放程序：：method_

为当前`Module::MethodReleaseNotifier`对象保留指向事件处理程序的指针。

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>模块：：方法释放程序：：方法释放器

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

*对象*<br/>
其成员函数为事件处理程序的对象。

*method*<br/>
参数*对象*的成员函数，即事件处理程序。

*释放*<br/>
指定`true`以启用调用基础[模块：：释放说明器：：：释放（）](module-releasenotifier-class.md#releasenotifier-release)方法;否则，指定`false`。

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>模块：：方法释放程序：：object_

保存指向其成员函数是当前`Module::MethodReleaseNotifier`对象的事件处理程序的对象的指针。

```cpp
T* object_;
```
