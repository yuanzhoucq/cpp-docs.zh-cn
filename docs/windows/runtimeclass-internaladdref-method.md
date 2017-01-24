---
title: "RuntimeClass::InternalAddRef 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::InternalAddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InternalAddRef 方法"
ms.assetid: b8ed7f93-83d8-47ec-988c-98fe65104e7a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::InternalAddRef 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

递增RuntimeClass当前对象的引用计数。  
  
## 语法  
  
```  
ULONG InternalAddRef();  
```  
  
## 返回值  
 生成的引用计数。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)