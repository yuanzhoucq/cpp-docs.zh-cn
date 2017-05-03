---
title: "WriteOnlyArray::FastPass 属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::FastPass"
dev_langs: 
  - "C++"
ms.assetid: f7a54ae0-afa0-4728-8736-c63933f789aa
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::FastPass 属性
指示能否执行内部 FastPass 优化。 不用于用户代码。  
  
## 语法  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
## 返回值  
 指示数组是否为 FastPass 的布尔值。  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)