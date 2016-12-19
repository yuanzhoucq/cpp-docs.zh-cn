---
title: "_com_ptr_t::AddRef | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::AddRef"
  - "_com_ptr_t.AddRef"
  - "AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法 [C++], 接口指针"
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::AddRef
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用封装的接口指针上的 **IUnknown** 的 `AddRef` 成员函数。  
  
## 语法  
  
```  
  
void AddRef( );  
  
```  
  
## 备注  
 如果封装的接口指针为 **NULL**，则在该指针上调用 `IUnknown::AddRef` 会引发 `E_POINTER` 错误。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)