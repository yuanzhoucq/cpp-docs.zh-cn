---
title: "HStringReference::HStringReference 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HStringReference::HStringReference 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 HStringReference 类的新实例。  
  
## 语法  
  
```cpp  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest],   
unsigned int len)  
       throw();  
  
    HStringReference(HStringReference&& other) throw();  
  
```  
  
#### 参数  
 `sizeDest`  
 指定目标 HStringReference 缓冲区大小的模板参数。  
  
 `str`  
 对字符串的引用。  
  
 `len`  
 使用参数的 `str` 缓冲区的最大长度此操作。  如果 `len` 参数没有指定，使用整个 `str` 参数。  如果 `len` 大于 `sizeDest`，`len` 设置为 `sizeDest`\-1。  
  
 `other`  
 另一 HStringReference 对象。  
  
## 备注  
 第一构造函数初始化的新 HStringReference 该对象的大小相同。参数 `str`。  
  
 第二个构造函数初始化的新 HStringReference 对象跨越 specifeid 由参数 `len`。  
  
 第三个构造函数初始化为 `other`参数的值的新 HStringReference 对象，然后会销毁 `other` 参数。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)