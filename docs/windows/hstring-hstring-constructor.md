---
title: "HString::HString 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::HString"
dev_langs: 
  - "C++"
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HString::HString 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 HString 类的新实例。  
  
## 语法  
  
```cpp  
  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### 参数  
 `hstr`  
 HSTRING 句柄。  
  
 `other`  
 一个现有的HString对象。  
  
## 备注  
 第一构造函数初始化空的新 HString 对象。  
  
 第二个构造函数初始化到现有的 `other` 参数值的新的对象，然后 HString 销毁 `other` 参数。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)