---
title: "编译器警告 (等级 1) C4744 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4744
dev_langs: C++
helpviewer_keywords: C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b6fa95f8477f889aa8664d2b6d99c753cb9848d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4744"></a>编译器警告（等级 1）C4744
var 具有 file1 和 file2 中的不同类型: type1 和 type2  
  
 在两个文件中定义或引用的外部变量，这些文件中具有不同的类型。  若要解决，请将类型定义相同，或者更改之一中的文件的变量名称。  
  
 仅当文件使用 /gl 进行编译时，发出 C4744  有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
> [!NOTE]
>  C4744 通常是在 C （不 c + +） 文件中，因为 c + + 中的变量名称修饰，使用类型信息。  （下面） 的示例是编译为 c + +，你会获得链接器错误 LNK2019。  
  
## <a name="example"></a>示例  
 此示例包含的第一个定义。  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>示例  
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