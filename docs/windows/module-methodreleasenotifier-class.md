---
title: 'Module:: methodreleasenotifier 类 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cee634ab62e699b4de6af54a57b0fe3d6b5e9a40
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606603"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 类

在释放当前模块中的最后一个对象时调用事件处理程序。 对象并将其指针到方法成员由指定的事件处理程序。

## <a name="syntax"></a>语法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>参数

*T*  
其成员函数是事件处理程序的对象的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::MethodReleaseNotifier 构造函数](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|初始化的新实例**module:: methodreleasenotifier**类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|调用与当前关联的事件处理程序**module:: methodreleasenotifier**对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[Module::MethodReleaseNotifier::method_ 数据成员](../windows/module-methodreleasenotifier-method-data-member.md)|包含当前的事件处理程序指向**module:: methodreleasenotifier**对象。|
|[Module::MethodReleaseNotifier::object_ 数据成员](../windows/module-methodreleasenotifier-object-data-member.md)|包含指向的成员函数是当前的事件处理程序对象**module:: methodreleasenotifier**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[Module 类](../windows/module-class.md)