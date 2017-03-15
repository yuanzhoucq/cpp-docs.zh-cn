---
title: "编译器警告（等级 1）C4005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4005"
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 宏重定义  
  
 宏标识符定义了两次。  编译器使用第二个宏定义。  
  
### 通过检查以下可能的原因进行修复  
  
1.  在命令行中以及在代码中用 `#define` 指令定义宏。  
  
2.  从包含文件导入的宏。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  移除其中一个定义。  
  
2.  在第二个定义之前使用 [\#undef](../../preprocessor/hash-undef-directive-c-cpp.md) 指令。  
  
 下面的示例生成 C4005：  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```