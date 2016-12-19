---
title: "如何：钉住指针和数组 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 钉住"
  - "指针, 钉住"
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：钉住指针和数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

固定在宿主的对象定义的子对象的固定整个对象的效果。例如，如果数组的任何元素使用锁定，然后整个数组也被锁定。  没有扩展名去声明固定数组的语言。  若要固定数组，请声明钉住的指针到其元素类型，并锁定元素之一。  
  
## 示例  
  
### 代码  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### Output  
  
```  
++  
```  
  
## 请参阅  
 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)