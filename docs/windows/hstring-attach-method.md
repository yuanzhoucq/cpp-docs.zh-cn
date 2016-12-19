---
title: "HString::Attach 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::Attach"
dev_langs: 
  - "C++"
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Attach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将指定的 HString 对象与当前的 HString 对象关联。  
  
## 语法  
  
```  
  
void Attach(  
       HSTRING hstr  
       ) throw()  
```  
  
#### 参数  
 `hstr`  
 一个现有的HString对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)