---
title: "include_alias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.include_alias"
  - "include_alias_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "include_alias 杂注"
  - "杂注, include_alias"
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# include_alias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 *short\_filename* 将用作 *long\_filename* 的别名。  
  
## 语法  
  
```  
  
      #pragma include_alias( "  
      long_filename  
      ", "  
      short_filename  
      " )  
#pragma include_alias( <long_filename>, <short_filename> )  
```  
  
## 备注  
 某些文件系统允许长度超过 8.3 FAT 文件系统限制的头文件名。  因为较长的头文件名的前八个字符可能不是唯一的，因此编译器无法简单地将较长的名称截断为 8.3。  每当编译器遇到 *long\_filename* 字符串时，都将替换 *short\_filename*，并改为查找头文件 *short\_filename*。  此杂注必须在相应的 `#include` 指令之前出现。  例如：  
  
```  
// First eight characters of these two files not unique.  
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )  
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )  
  
#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )  
  
#include "AppleSystemHeaderQuickdraw.h"  
#include "AppleSystemHeaderFruit.h"  
#include "GraphicsMenu.h"  
```  
  
 要搜索的别名必须完全符合规范，无论是大小写、拼写还是双引号或尖括号的使用。  **include\_alias** 杂注对文件名执行简单的字符串匹配；将不执行任何其他文件名验证。  例如，给定下列指令，  
  
```  
#pragma include_alias("mymath.h", "math.h")  
#include "./mymath.h"  
#include "sys/mymath.h"  
```  
  
 将不执行指定别名（替换）操作，因为头文件字符串不完全匹配。  此外，将不会替换用作 \/Yu 和 \/Yc 编译器选项参数的头文件名或 **hdrstop** 杂注。  例如，如果源文件包含以下指令，  
  
```  
#include <AppleSystemHeaderStop.h>  
```  
  
 则相应的编译器选项应为  
  
```  
/YcAppleSystemHeaderStop.h  
```  
  
 您可以使用 **include\_alias** 杂注将任何头文件名映射到另一个头文件名。  例如：  
  
```  
#pragma include_alias( "api.h", "c:\version1.0\api.h" )  
#pragma include_alias( <stdio.h>, <newstdio.h> )  
#include "api.h"  
#include <stdio.h>  
```  
  
 不要将用双引号括起来的文件名与用尖括号括起的文件名组合在一起。  例如，给定上述两个 **\#pragma include\_alias** 指令，编译器将不对下列 `#include` 指令执行任何替换：  
  
```  
#include <api.h>  
#include "stdio.h"  
```  
  
 而且，以下指令将生成错误：  
  
```  
#pragma include_alias(<header.h>, "header.h")  // Error  
```  
  
 请注意，错误消息中报告的文件名（或作为预定义的 **\_\_FILE\_\_** 宏的值的文件名）是文件在执行替换后的名称。  例如，在下列指令之后，  
  
```  
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )  
#include "VeryLongFileName.H"  
```  
  
 VERYLONGFILENAME.H 中的错误将产生以下错误消息：  
  
```  
myfile.h(15) : error C2059 : syntax error  
```  
  
 请注意，不支持传递性。  给定以下指令，  
  
```  
#pragma include_alias( "one.h", "two.h" )  
#pragma include_alias( "two.h", "three.h" )  
#include "one.h"  
```  
  
 编译器将搜索文件 TWO.H 而不是 THREE.H。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)