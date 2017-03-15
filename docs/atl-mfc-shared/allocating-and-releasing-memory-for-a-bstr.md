---
title: "Allocating and Releasing Memory for a BSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "bstr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, 内存分配"
  - "内存 [C++], 释放"
  - "内存分配, BSTR"
  - "memory deallocation, BSTR memory"
  - "memory deallocation, string memory"
  - "字符串 [C++], 释放"
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Allocating and Releasing Memory for a BSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当您创建 `BSTR`的并将它们使用以避免内存泄漏的它们在COM对象之间时，必须注意在将内存的。  当 `BSTR` 在接口中保持，必须释放其内存，当处理它。  但是，那么，当 `BSTR` 通过在接口外时，接收的对象对其内存管理的责任。  
  
 通常，分配和释放为 `BSTR`分配的内存的规则如下:  
  
-   在您调用需要 `BSTR` 参数的函数时，必须在调用之前分配 `BSTR` 的内存和之后释放。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   在您调用返回 `BSTR`的函数时，必须释放字符串。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   在实现返回 `BSTR`的函数时，将字符串，但不要释放它。  接收函数释放内存。  例如：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/CPP/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)   
 [SysAllocString](http://msdn.microsoft.com/zh-cn/9e0437a2-9b4a-4576-88b0-5cb9d08ca29b)   
 [SysFreeString](http://msdn.microsoft.com/zh-cn/8f230ee3-5f6e-4cb9-a910-9c90b754dcd3)