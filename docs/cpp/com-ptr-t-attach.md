---
title: "_com_ptr_t::Attach | Microsoft Docs"
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
  - "_com_ptr_t::Attach"
  - "_com_ptr_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
  - "COM 接口, 附加指针"
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 封装此智能指针的类型的原始接口指针。  
  
## 语法  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### 参数  
 `pInterface`  
 原始接口指针。  
  
 `fAddRef`  
 如果它是 **true**，则调用 `AddRef`。  如果它是 **false**，则 `_com_ptr_t` 对象将拥有原始接口指针的所有权，而不调用 `AddRef`。  
  
## 备注  
  
-   **Attach\(**  `pInterface`  **\)** 未调用 `AddRef`。  将接口的所有权传递给此 `_com_ptr_t` 对象。  调用 **Release** 以减少前面封装的指针的引用计数。  
  
-   **Attach\(**  `pInterface` **,**  `fAddRef`  **\)** 如果 `fAddRef` 为 **true**，则调用 `AddRef` 来增加封装的接口指针的引用计数。  如果 `fAddRef` 为 **false**，则 `_com_ptr_t` 对象将拥有原始接口指针的所有权，而不调用 `AddRef`。  调用 **Release** 以减少前面封装的指针的引用计数。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)