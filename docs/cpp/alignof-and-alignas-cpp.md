---
title: "alignof 和 alignas (C++) | Microsoft Docs"
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
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# alignof 和 alignas (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`alignas` 类型说明符是用于指定变量和用户定义类型的自定义对齐方式的一种可移植的 C\+\+ 标准方法。  `alignof` 运算符也是一种获取指定类型或变量的对齐方式的标准可移植的方法。  
  
## 示例  
 你可以在类（struck 或 union）或者单个成员上使用 `alignas`。  遇到多个 `alignas` 说明符时，编译器将选择最严格的说明符（即具有最大值的说明符）。  
  
```  
struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  
…  
cout << alignof(Bar) << endl; // output: 16  
  
```  
  
## 请参阅  
 [对齐](../cpp/alignment-cpp-declarations.md)