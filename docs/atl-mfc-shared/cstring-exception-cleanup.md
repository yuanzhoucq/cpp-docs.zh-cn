---
title: "CString Exception Cleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CString objects, 异常"
  - "异常处理, cleanup code"
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CString Exception Cleanup
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在MFC的早期版本中，务必要清理 [CString](../atl-mfc-shared/reference/cstringt-class.md) 对象使用之后。  MFC 3.0版或更高，显式清除不再是必需的。  
  
 在MFC现在使用的C\+\+异常处理机制下，不必担心清理在异常后。  有关说明C\+\+ “如何”展开堆栈，在捕获到异常后，请参见 [尝试、捕获和throw语句](../cpp/try-throw-and-catch-statements-cpp.md)。  即使您使用MFC **TRY**\/**CATCH** 宏而不是C\+\+关键字 **try** 和 **catch**，MFC下方使用C\+\+异常结构，因此，您仍不需要显式清理。  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)   
 [异常处理](../mfc/exception-handling-in-mfc.md)