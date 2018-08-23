---
title: 'Module:: releasenotifier:: 调用方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: f62686fe-74bf-482b-a46b-6a3c09b80e7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da71ab887145f3bcb1341b5ea6004a24253a4a5f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594495"
---
# <a name="modulereleasenotifierinvoke-method"></a>Module::ReleaseNotifier::Invoke 方法

实现后，在释放模块中的最后一个对象时调用事件处理程序。

## <a name="syntax"></a>语法

```cpp
virtual void Invoke() = 0;
```

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)