---
title: "HStringReference::CopyTo 方法 | Microsoft Docs"
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
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HStringReference::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制到 HSTRING 对象的当前 HStringReference 对象。  
  
## 语法  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### 参数  
 `str`  
 防止该副本的 HSTRING。  
  
## 备注  
 此方法调用函数。[WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx)  
  
## 要求  
 **页眉：**corewrappers.h  
  
 **命名空间 \(N\):** Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)