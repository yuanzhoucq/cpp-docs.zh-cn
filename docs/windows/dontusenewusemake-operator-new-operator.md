---
title: "DontUseNewUseMake::operator new 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator new 运算符"
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# DontUseNewUseMake::operator new 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### 参数  
 `__unnamed0`  
 指定的内存分配的未命名参数。  
  
 `placement`  
 要分配的类型。  
  
## 返回值  
 如果重载operator `new`，则提供了一种传递附加参数的方式。  
  
## 备注  
 在 RuntimeClass 重载运算符 `new` 并防止它。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [DontUseNewUseMake 类](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)