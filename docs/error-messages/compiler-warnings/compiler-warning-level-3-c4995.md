---
title: "编译器警告（等级 3）C4995 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4995"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4995"
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 3）C4995
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 名称被标记为 \#pragma deprecated  
  
 编译器遇到了标记有杂注 [deprecated](../../preprocessor/deprecated-c-cpp.md) 的函数。  在未来版本中可能不再支持此函数。  可以用 [warning](../../preprocessor/warning.md) 杂注关闭此警告（如下例所示）。  
  
## 示例  
 下面的示例生成 C4995：  
  
```  
// C4995.cpp  
// compile with: /W3  
#include <stdio.h>  
  
// #pragma warning(disable : 4995)  
void func1(void)  
{  
    printf("\nIn func1");  
}  
  
int main()   
{  
    func1();  
    #pragma deprecated(func1)  
    func1();   // C4995  
}  
```