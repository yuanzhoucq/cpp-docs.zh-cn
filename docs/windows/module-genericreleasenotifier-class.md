---
title: "Module::GenericReleaseNotifier 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::GenericReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GenericReleaseNotifier 类"
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::GenericReleaseNotifier 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由 lambda、functor 或 pointer-to-function 指定。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 包含事件处理程序位置的数据成员的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|初始化 Module::GenericReleaseNotifier 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module:: genericreleasenotifier:: Invoke 方法](../windows/module-genericreleasenotifier-invoke-method.md)|调用与当前 Module::GenericReleaseNotifier 对象关联的事件处理程序。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ 数据成员](../windows/module-genericreleasenotifier-callback-data-member.md)|包含与当前 Module::GenericReleaseNotifier 对象关联的 lambda、functor 或 pointer-to-function 事件处理程序。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)