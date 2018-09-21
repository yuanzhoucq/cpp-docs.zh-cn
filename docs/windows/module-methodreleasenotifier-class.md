---
title: 'Module:: methodreleasenotifier 类 |Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e78542e016ab0ba8ef33a5655b72fcdff45ccc4
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494447"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 类

在释放当前模块中的最后一个对象时调用事件处理程序。 对象并将其指针到方法成员由指定的事件处理程序。

## <a name="syntax"></a>语法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>参数

*T*<br/>
其成员函数是事件处理程序的对象的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                                                 | 描述
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | 初始化 `Module::MethodReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                                   | 描述
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module:: methodreleasenotifier:: 调用](#methodreleasenotifier-invoke) | 调用与当前关联的事件处理程序`Module::MethodReleaseNotifier`对象。

### <a name="protected-data-members"></a>受保护的数据成员

name                                                                    | 描述
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | 包含当前的事件处理程序指向`Module::MethodReleaseNotifier`对象。
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | 包含指向对象的成员函数是当前的事件处理程序`Module::MethodReleaseNotifier`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module:: methodreleasenotifier:: 调用

调用与当前关联的事件处理程序`Module::MethodReleaseNotifier`对象。

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

包含当前的事件处理程序指向`Module::MethodReleaseNotifier`对象。

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

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

*object*  
一个对象，其成员函数为事件处理程序。

*方法*  
成员函数的参数*对象*，它是事件处理程序。

*release*  
指定`true`若要启用调用基础[模块:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release)方法; 否则，请指定`false`。

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

包含指向对象的成员函数是当前的事件处理程序`Module::MethodReleaseNotifier`对象。

```cpp
T* object_;
```
