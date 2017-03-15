---
title: "hdrstop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hdrstop_CPP"
  - "vc-pragma.hdrstop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hdrstop 杂注"
  - "杂注, hdrstop"
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# hdrstop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供对预编译文件名和编译状态的保存位置的额外控制。  
  
## 语法  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## 备注  
 *filename* 是要使用或创建的预编译头文件的名称（取决于是否指定 [\/Yu](../build/reference/yu-use-precompiled-header-file.md) 或 [\/Yc](../build/reference/yc-create-precompiled-header-file.md)）。  如果 *filename* 不包含路径说明，则假定预编译头文件位于源文件所在的同一目录中。  
  
 当用 \/Yc 编译时，如果 C 或 C\+\+ 文件包含 **hdrstop** 杂注，则编译器将保存编译状态，直到到达杂注位置。  不会保存遵循杂注的任何代码的编译状态。  
  
 使用 *filename* 命名将编译状态保存到的预编译头文件。  **hdrstop** 和 *filename* 之间的空格是可选的。  **hdrstop** 杂注中指定的文件名是字符串，并且受任何 C 或 C\+\+ 字符串的约束。  具体来说，您必须将其包含在引号中并使用转义符（反斜杠）来指定目录名称。  例如：  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 预编译头文件的名称是根据以下规则按优先顺序决定的。  
  
1.  \/Fp 编译器选项的参数  
  
2.  \#**pragma hdrstop** 的 *filename* 参数  
  
3.  扩展名为 .PCH 的源文件基名称  
  
 对于 \/Yc 和 \/Yu 选项，如果两个编译选项和 **hdrstop** 杂注都未指定文件名，则将源文件的基名称用作预编译头文件的基名称。  
  
 还可以使用预处理命令来执行宏替换，如下所示：  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 以下规则管理可将 **hdrstop** 杂注放置到的位置：  
  
-   它必须出现在任何数据或函数声明\/定义的外部。  
  
-   必须在源文件而不是头文件中指定它。  
  
## 示例  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 在此示例中，**hdrstop** 杂注会在已包含两个文件并且已定义内联函数后出现。  最初，这可能是杂注的临时位置。  但请考虑，通过将手动预编译选项 \/Yc 和 \/Yu 与 **hdrstop** 杂注结合使用，您可以预编译整个源文件 \- 甚至是内联代码。  Microsoft 编译器不会只允许您预编译数据声明。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)