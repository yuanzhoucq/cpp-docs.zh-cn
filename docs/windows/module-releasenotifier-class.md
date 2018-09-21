---
title: 'Module:: releasenotifier 类 |Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c9af03549eec7b62cc34aec2840764c54d2a21e
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494356"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 类

在释放模块中的最后一个对象时调用事件处理程序。

## <a name="syntax"></a>语法

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                                | 描述
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: releasenotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 取消初始化的当前实例`Module::ReleaseNotifier`类。
[Module::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                         | 描述
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: releasenotifier:: 调用](#releasenotifier-invoke)   | 实现后，在释放模块中的最后一个对象时调用事件处理程序。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 删除当前`Module::ReleaseNotifier`对象如果对象使用参数的构造`true`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: releasenotifier:: ~ ReleaseNotifier

取消初始化的当前实例`Module::ReleaseNotifier`类。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: releasenotifier:: 调用

实现后，在释放模块中的最后一个对象时调用事件处理程序。

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

删除当前`Module::ReleaseNotifier`对象如果对象使用参数的构造`true`。

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::ReleaseNotifier::ReleaseNotifier

初始化 `Module::ReleaseNotifier` 类的新实例。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>参数

*release*  
`true` 若要删除此实例时`Release`调用方法;`false`不删除此实例。
