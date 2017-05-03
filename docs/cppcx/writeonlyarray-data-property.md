---
title: "WriteOnlyArray::Data 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::Data"
dev_langs: 
  - "C++"
ms.assetid: 6db4b513-eae8-4d82-b190-b90e16aeb202
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::Data 属性
指向数据缓冲区的指针。  
  
## 语法  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
## 返回值  
 指向原始数组字节的指针。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)