---
title: "编译器警告（等级 1）C4742 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4742"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4742"
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4742
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”在“file1”和“file2”中具有不同的对齐: number 和 number  
  
 在两个文件中，引用或定义的外部变量在这些文件中具有不同的对齐。  这个警告当在编译器发现 `__alignof`的变量*file1* 和 `__alignof`的变量 *file2*不同时才会报出。  导致此错误发生的原因可能是：在不同文件中声明变量时使用了不兼容的类型，或是在不同文件中使用了不匹配的 `#pragma pack`。  
  
 若要解除此警告，请使用相同类型的定义，或为变量使用不同的名称。  
  
 有关更多信息，请参见[pack](../../preprocessor/pack.md)和[\_\_alignof 运算符](../../cpp/alignof-operator.md)。  
  
## 示例  
 这是定义类型的第一个文件。  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## 示例  
 下面的示例生成 C4742。  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```