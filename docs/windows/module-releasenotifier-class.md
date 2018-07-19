---
title: 'Module:: releasenotifier 类 |Microsoft 文档'
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
ms.openlocfilehash: 76edb403fae12dd8b6221d8bd6ec82424bc5a4f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878387"
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
|[Module::ReleaseNotifier::~ReleaseNotifier 析构函数](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|取消初始化 Module::ReleaseNotifier 类的当前实例。|  
|[Module::ReleaseNotifier::ReleaseNotifier 构造函数](../windows/module-releasenotifier-releasenotifier-constructor.md)|初始化 Module::ReleaseNotifier 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke 方法](../windows/module-releasenotifier-invoke-method.md)|实现后，在释放模块中的最后一个对象时调用事件处理程序。|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|如果对象是使用 `true` 的参数构造的，则删除当前 Module::ReleaseNotifier 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)