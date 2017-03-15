---
title: "HString::CopyTo 方法 | Microsoft Docs"
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
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HString::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将当前 HString 对象复制到 HSTRING 对象。  
  
## 语法  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### 参数  
 `str`  
 接收副本的 HSTRING。  
  
## 备注  
 此方法调用 [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) 函数。  
  
## 要求  
 **头文件：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)