---
title: "HString::MakeReference 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference"
dev_langs: 
  - "C++"
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::MakeReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从指定的字符串参数创建 HStringReference 对象。  
  
## 语法  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### 参数  
 `sizeDest`  
 指定目标 HStringReference 缓冲区大小的模板参数。  
  
 `str`  
 对字符串的引用。  
  
 `len`  
 使用参数的 `str` 缓冲区的最大长度此操作。  如果 `len` 参数没有指定，使用整个 `str` 参数。  
  
## 返回值  
 值与指定的 `str` 参数的 HStringReference 对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)