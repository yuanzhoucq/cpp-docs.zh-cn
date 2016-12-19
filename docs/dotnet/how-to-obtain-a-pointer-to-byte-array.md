---
title: "如何：获取字节数组的指针 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Byte 数组"
  - "指针, 指向 Byte 数组"
ms.assetid: aea18073-3341-47f4-9f0e-04e03327037e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：获取字节数组的指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过获取第一个元素的地址并将其分配给指针，可以获取指向 <xref:System.Byte> 数组中的数组块的指针。  
  
## 示例  
  
```  
// pointer_to_Byte_array.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Byte bArr[] = {1, 2, 3};  
   Byte* pbArr = &bArr[0];  
  
   array<Byte> ^ bArr2 = gcnew array<Byte>{1,2,3};  
   interior_ptr<Byte> pbArr2 = &bArr2[0];  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)