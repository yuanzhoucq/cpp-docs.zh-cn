---
title: 'Module:: releasenotifier:: Invoke 方法 |Microsoft 文档'
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
ms.openlocfilehash: 6eb51d59d2f7f1adc934332cbfa5fead56bbef0a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876197"
---
# <a name="modulereleasenotifierinvoke-method"></a>Module::ReleaseNotifier::Invoke 方法
实现后，在释放模块中的最后一个对象时调用事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
virtual void Invoke() = 0;  
```  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)