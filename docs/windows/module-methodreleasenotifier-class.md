---
title: "Module:: methodreleasenotifier 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs: C++
helpviewer_keywords: MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 113ea9179292606461a8fe67ff161f63e58161da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 类
在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由对象并将其指针到方法成员指定。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 其成员函数是事件处理程序的对象的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier 构造函数](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|初始化 module:: methodreleasenotifier 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|调用与当前 module:: methodreleasenotifier 对象相关联的事件处理程序。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ 数据成员](../windows/module-methodreleasenotifier-method-data-member.md)|包含指向当前 Module::MethodReleaseNotifier 对象的事件处理程序的指针。|  
|[Module::MethodReleaseNotifier::object_ 数据成员](../windows/module-methodreleasenotifier-object-data-member.md)|包含指向其成员函数是当前 Module::MethodReleaseNotifier 对象的事件处理程序的对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)