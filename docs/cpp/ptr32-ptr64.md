---
title: "__ptr32、__ptr64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__ptr32_cpp"
  - "__ptr64_cpp"
  - "__ptr32"
  - "__ptr64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ptr32 关键字 [C++]"
  - "__ptr64 关键字 [C++]"
  - "_ptr32 关键字 [C++]"
  - "_ptr64 关键字 [C++]"
  - "ptr32 关键字 [C++]"
  - "ptr64 关键字 [C++]"
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# __ptr32、__ptr64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `__ptr32` 表示 32 位系统中的本机指针，而 `__ptr64` 表示 64 位系统中的本机指针。  
  
 以下示例演示如何声明所有这些指针类型：  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 在 32 位系统中，使用 `__ptr64` 声明的指针被截断为 32 位指针。  在 64 位系统中, 使用 `__ptr32` 声明的指针被强制转换为 64 位指针。  
  
> [!NOTE]
>  当使用 `__ptr32` 进行编译时，不能使用 `__ptr64` 或 **\/clr:pure**。  否则，将生成 `Compiler Error C2472`。  
  
## 示例  
 以下示例演示如何使用 `__ptr32` 和 `__ptr64` 关键字声明和分配指针。  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
  **32**  
**64**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [基本类型](../cpp/fundamental-types-cpp.md)