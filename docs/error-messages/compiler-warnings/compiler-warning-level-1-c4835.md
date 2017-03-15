---
title: "编译器警告（等级 1）C4835 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4835"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4835"
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器警告（等级 1）C4835
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: 在主机程序集中首次执行托管代码之后，才能运行导出数据的初始值设定项  
  
 在托管组件之间访问数据时，建议不要使用本机 C\+\+ 导入和导出机制。  而应在托管类型内声明数据成员，并在客户端中使用 `#using` 引用该元数据。  有关详细信息，请参阅[\#using 指令](../../preprocessor/hash-using-directive-cpp.md)。  
  
## 示例  
 下面的示例生成 C4835。  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## 示例  
 下面的示例使用上一示例中生成的组件，演示变量的值不是所期望的值。  
  
```  
// C4835_b.cpp  
// compile with: /clr C4835.lib  
#include <stdio.h>  
__declspec(dllimport) int m;  
__declspec(dllimport) int *p;  
  
int main() {  
   printf("%d\n", m);  
   printf("%d\n", p);  
}  
```  
  
  **0**  
**268456008**