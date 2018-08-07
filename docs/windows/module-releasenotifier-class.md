---
title: 'Module:: releasenotifier 类 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1deeb3076d3f1bfc2243ec333f258f543a37fceb
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608386"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 类
在释放模块中的最后一个对象时调用事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier 析构函数](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|取消初始化的当前实例**module:: releasenotifier**类。|  
|[Module::ReleaseNotifier::ReleaseNotifier 构造函数](../windows/module-releasenotifier-releasenotifier-constructor.md)|初始化的新实例**module:: releasenotifier**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke 方法](../windows/module-releasenotifier-invoke-method.md)|实现后，在释放模块中的最后一个对象时调用事件处理程序。|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|删除当前**module:: releasenotifier**对象如果对象使用参数的构造**true**。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)