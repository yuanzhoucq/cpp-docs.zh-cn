---
title: "如何：取消装箱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "取消装箱"
ms.assetid: 75794696-9275-47bf-9a7d-5abe6585ab91
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 如何：取消装箱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

演示如何取消装箱和修改值。  
  
## 示例  
  
```  
// vcmcppv2_unboxing.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   int ^ i = gcnew int(13);  
   int j;  
   Console::WriteLine(*i);   // unboxing  
   *i = 14;   // unboxing and assignment  
   Console::WriteLine(*i);  
   j = safe_cast<int>(i);   // unboxing and assignment  
   Console::WriteLine(j);  
}  
```  
  
  **13**  
**14**  
**14**   
## 请参阅  
 [装箱](../windows/boxing-cpp-component-extensions.md)