---
title: "Implements::FillArrayWithIid 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于插入当前 zeroth 模板参数指定的接口 ID 到指定的数组元素。  
  
## 语法  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### 参数  
 `index`  
 指示此操作的开始数组元素的从零开始的索引。  当完成此操作时，由 `index` 1. 增加。  
  
 `iids`  
 类型IID数组。  
  
## 备注  
 内部帮助器函数。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Implements 结构](../windows/implements-structure.md)