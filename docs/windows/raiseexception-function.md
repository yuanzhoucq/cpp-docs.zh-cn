---
title: "RaiseException 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::RaiseException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RaiseException 函数"
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RaiseException 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
inline void __declspec(noreturn)  
   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### 参数  
 `hr`  
 引发异常；异常的代码即不合格操作的 HRESULT。  
  
 `dwExceptionFlags`  
 指示可继续异常的标志 \(标志值零\)，或者 noncontinuable 异常 \(标志值是非零\)。   默认情况下，noncontinuable 异常。  
  
## 备注  
 引发在调用线程上的异常。  
  
 有关Windows **RaiseException** 函数的详细信息，请参阅 。  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)