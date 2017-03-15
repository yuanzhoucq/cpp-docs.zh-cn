---
title: "Module::MethodReleaseNotifier::MethodReleaseNotifier 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MethodReleaseNotifier, 构造函数"
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Module::MethodReleaseNotifier::MethodReleaseNotifier 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module::MethodReleaseNotifier 类的新实例。  
  
## 语法  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### 参数  
 `object`  
 成员函数是事件处理程序的对象。  
  
 `method`  
 为事件处理程序参数的 `object` 成员函数。  
  
 `release`  
 指定 `true` 允许以 [Module::ReleaseNotifier:: Release\(\)](../windows/module-releasenotifier-release.md) 基础方法；否则，请改为指定 `false`。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Module::MethodReleaseNotifier 类](../windows/module-methodreleasenotifier-class.md)