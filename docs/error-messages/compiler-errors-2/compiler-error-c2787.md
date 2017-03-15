---
title: "编译器错误 C2787 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2787"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2787"
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2787
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 没有与此对象关联的 GUID  
  
 [\_\_uuidof](../../cpp/uuidof-operator.md) 运算符采用附加了 GUID 的用户定义类型，或采用这种用户定义类型的对象。  当参数是不具有 GUID 的用户定义的类型时，发生此错误。  
  
 下面的示例生成 C2787：  
  
```  
// C2787.cpp  
#include <windows.h>  
struct F {};  
  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;  
  
int main() {  
   __uuidof(F);   // C2787  
   __uuidof(F2);   // OK  
}  
```