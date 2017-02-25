---
title: "编译器警告（等级 1）C4744 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4744"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4744"
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4744
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”在“file1”和“file2”中具有不同的类型:“type1”和“type2”  
  
 这两个文件中引用或定义的外部变量在这些文件中具有不同的类型。若要解决此问题，请将类型定义设置为相同，或更改其中某个文件中的变量名。  
  
 仅在使用 \/GL 编译文件时发出 C4744 警告。有关详细信息，请参阅[\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
> [!NOTE]
>  C4744 通常出现在 C（而不是 C\+\+）文件中，因为在 C\+\+ 中，变量名是用类型信息修饰的。当以 C\+\+ 编译下面的示例时，您将收到链接器错误 LNK2019。  
  
## 示例  
 此示例包含第一个定义。  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## 示例  
 下面的示例生成 C4744。  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```