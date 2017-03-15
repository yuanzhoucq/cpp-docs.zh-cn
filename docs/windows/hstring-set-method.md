---
title: "HString::Set 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::Set"
dev_langs: 
  - "C++"
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HString::Set 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将当前 HString 对象的值设置为指定的宽字符串或 HString 参数。  
  
## 语法  
  
```  
  
HRESULT Set(  
          const wchar_t* str) throw();  
HRESULT Set(   
          const wchar_t* str,   
          unsigned int len  
           ) throw();  
HRESULT Set(  
          const HSTRING& hstr  
           ) throw();  
```  
  
#### 参数  
 `str`  
 宽字符字符串。  
  
 `len`  
 分配给当前 HString 对象 `str` 参数的最大长度。  
  
 `hstr`  
 一个现有的HString对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)