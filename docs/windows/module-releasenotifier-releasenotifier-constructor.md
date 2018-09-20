---
title: Module::ReleaseNotifier::ReleaseNotifier 构造函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e43abd46ccfb150936ff435360611289f18a1270
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405016"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier 构造函数

初始化的新实例**module:: releasenotifier**类。

## <a name="syntax"></a>语法

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>参数

*release*<br/>
**true**若要删除此实例时`Release`调用方法;**false**不删除此实例。

## <a name="exceptions"></a>异常

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)