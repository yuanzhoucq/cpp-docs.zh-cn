---
title: "WeakRef::operator&amp; 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::operator&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator& 运算符"
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::operator&amp; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回一个表示当前 WeakRef 对象的 ComPtrRef 对象。  
  
## 语法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## 返回值  
 返回一个表示当前 WeakRef 对象的 ComPtrRef 对象 。  
  
## 备注  
 这是不会在代码的内部帮助器运算符。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [WeakRef 类](../windows/weakref-class.md)