---
title: 'Module:: genericreleasenotifier 类 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80b04600f1f464220b00749903f27826855f6000
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400258"
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

|名称|描述|
|----------|-----------------|
|[Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|初始化的新实例**module:: genericreleasenotifier**类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Module::GenericReleaseNotifier::Invoke 方法](../windows/module-genericreleasenotifier-invoke-method.md)|调用与当前关联的事件处理程序**module:: genericreleasenotifier**对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[Module::GenericReleaseNotifier::callback_ 数据成员](../windows/module-genericreleasenotifier-callback-data-member.md)|包含 lambda、 functor 或函数指针事件处理程序与当前相关联**module:: genericreleasenotifier**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)