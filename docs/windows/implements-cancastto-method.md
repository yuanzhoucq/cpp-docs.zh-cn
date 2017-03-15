---
title: "Implements::CanCastTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo 方法"
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::CanCastTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取特定接口的指针。  
  
## 语法  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### 参数  
 `riid`  
 对接口 ID的引用  
  
 `ppv`  
 如果成功，指向 `riid`指定的接口。  
  
## 返回值  
 S\_OK，如果成功；否则，一 HRESULT 指示的错误，如。E\_NOINTERFACE  
  
## 备注  
 这是运行的 QueryInterface 操作的内部帮助器函数。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Implements 结构](../windows/implements-structure.md)