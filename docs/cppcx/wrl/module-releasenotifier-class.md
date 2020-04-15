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
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371278"
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
[模块：：释放器：：*释放器](#releasenotifier-tilde-releasenotifier) | 取消初始化类的`Module::ReleaseNotifier`当前实例。
[模块：：释放程序：：释放器](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                         | 说明
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[模块：：释放程序：：调用](#releasenotifier-invoke)   | 实现后，在释放模块中的最后一个对象时调用事件处理程序。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 如果对象构造的`Module::ReleaseNotifier`参数为**true**，则删除当前对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>模块：：释放器：：*释放器

取消初始化类的`Module::ReleaseNotifier`当前实例。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>模块：：释放程序：：调用

实现后，在释放模块中的最后一个对象时调用事件处理程序。

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>模块：：发布程序：：发布

如果对象构造的`Module::ReleaseNotifier`参数为**true**，则删除当前对象。

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>模块：：释放程序：：释放器

初始化 `Module::ReleaseNotifier` 类的新实例。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>参数

*释放*<br/>
`true`在调用`Release`方法时删除此实例;`false`不删除此实例。
