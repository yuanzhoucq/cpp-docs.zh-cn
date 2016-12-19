---
title: "Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GenericReleaseNotifier, 构造函数"
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化Module::GenericReleaseNotifier类的新实例。  
  
## 语法  
  
```  
GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### 参数  
 `callback`  
 可以使用圆括号调用运算符的 lambda 函数、functor 指针到函数或事件处理程序 \(`()`\)。  
  
 `release`  
 指定 `true` 允许以 [Module::ReleaseNotifier:: Release\(\)](../windows/module-releasenotifier-release.md) 基础方法；否则，请改为指定 `false`。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Module::GenericReleaseNotifier 类](../windows/module-genericreleasenotifier-class.md)