---
title: Module::ReleaseNotifier 类
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423626"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 类

在释放模块中的最后一个对象时调用事件处理程序。

## <a name="syntax"></a>语法

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                                | 说明
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module：： ReleaseNotifier：： ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 取消初始化 `Module::ReleaseNotifier` 类的当前实例。
[Module：： ReleaseNotifier：： ReleaseNotifier](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                         | 说明
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module：： ReleaseNotifier：： Invoke](#releasenotifier-invoke)   | 实现后，在释放模块中的最后一个对象时调用事件处理程序。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 如果对象是用**true**的参数构造的，则删除当前的 `Module::ReleaseNotifier` 对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module：： ReleaseNotifier：： ~ ReleaseNotifier

取消初始化 `Module::ReleaseNotifier` 类的当前实例。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module：： ReleaseNotifier：： Invoke

实现后，在释放模块中的最后一个对象时调用事件处理程序。

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module：： ReleaseNotifier：： Release

如果对象是用**true**的参数构造的，则删除当前的 `Module::ReleaseNotifier` 对象。

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module：： ReleaseNotifier：： ReleaseNotifier

初始化 `Module::ReleaseNotifier` 类的新实例。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>parameters

*release*<br/>
`true` 在调用 `Release` 方法时删除此实例;`false` 不删除此实例。
