---
title: "Implements::CastToUnknown 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown 方法"
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::CastToUnknown 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一个指向基础 IUnknown 接口。  
  
## 语法  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## 返回值  
 此运算始终成功并返回由指针。  
  
## 备注  
 内部帮助器函数。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Implements 结构](../windows/implements-structure.md)