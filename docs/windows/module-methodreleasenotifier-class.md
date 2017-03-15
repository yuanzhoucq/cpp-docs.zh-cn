---
title: "Module::MethodReleaseNotifier 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::MethodReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MethodReleaseNotifier 类"
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::MethodReleaseNotifier 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在释放当前模块中的最后一个对象时调用事件处理程序。 对象和它的指针到方法成员由指定的事件处理程序。  
  
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
|[Module:: methodreleasenotifier:: Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|调用与当前 module:: methodreleasenotifier 对象关联的事件处理程序。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ 数据成员](../windows/module-methodreleasenotifier-method-data-member.md)|包含指向当前 Module::MethodReleaseNotifier 对象的事件处理程序的指针。|  
|[Module::MethodReleaseNotifier::object_ 数据成员](../windows/module-methodreleasenotifier-object-data-member.md)|包含指向其成员函数是当前 Module::MethodReleaseNotifier 对象的事件处理程序的对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)