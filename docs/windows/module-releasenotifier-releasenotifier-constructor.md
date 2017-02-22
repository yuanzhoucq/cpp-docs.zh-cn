---
title: "Module::ReleaseNotifier::ReleaseNotifier 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseNotifier, 构造函数"
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Module::ReleaseNotifier::ReleaseNotifier 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module::ReleaseNotifie 类的新实例。  
  
## 语法  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### 参数  
 `release`  
 删除该实例的`true`，在释放调用方法；删除该实例的 `false`。  
  
## 异常  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)