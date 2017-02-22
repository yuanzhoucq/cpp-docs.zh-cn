---
title: "ComPtr::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::Reset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放所有指向与此 ComPtr 相关联的接口的指针的引用。  
  
## 语法  
  
```  
unsigned long Reset();  
```  
  
## 返回值  
 已释放的引用的数量（如果存在）。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)