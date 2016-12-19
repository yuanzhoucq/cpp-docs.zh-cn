---
title: "C++ 中的全局常量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常量, 全局"
  - "全局常量"
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 中的全局常量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C\+\+ 全局常数具有静态链接。  这与 C 不同。  如果尝试在多个文件中使用 C\+\+ 全局常数，将得到无法解析的外部错误。  编译器优化掉全局常数，不留下为变量保留的空间。  
  
 解决此错误的一种方法是将常数初始化包含在头文件中，并在需要时将该头包含在 CPP 文件中，就像它是函数原型一样。  另一种可能的方法是使变量成为非常数，并在访问变量时使用常数引用。  
  
 下面的示例生成 C2019：  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 然后，  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## 请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)