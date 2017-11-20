---
title: "hdrstop |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs: C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: be26e2139ab0cf0e31e63331a8e87df8769fe715
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="hdrstop"></a>hdrstop
提供对预编译文件名和编译状态的保存位置的额外控制。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>备注  
 *Filename*是要使用或创建的预编译标头文件的名称 (具体取决于是否[/Yu](../build/reference/yu-use-precompiled-header-file.md)或[/Yc](../build/reference/yc-create-precompiled-header-file.md)指定)。 如果*filename*不包含路径说明，则假定预编译标头文件位于源文件所在相同目录中。  
  
 如果 C 或 c + + 文件包含**hdrstop**杂注用 /Yc 编译时，编译器将保存到杂注位置编译的状态。 不会保存遵循杂注的任何代码的编译状态。  
  
 使用*filename*命名的编译的状态保存在其中预编译标头文件。 之间留一个空格**hdrstop**和*filename*是可选的。 中指定的文件名称**hdrstop**杂注是一个字符串，并且受任何 C 或 c + + 字符串的约束。 具体来说，您必须将其包含在引号中并使用转义符（反斜杠）来指定目录名称。 例如：  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 预编译头文件的名称是根据以下规则按优先顺序决定的。  
  
1.  /Fp 编译器选项的自变量  
  
2.  *Filename*参数 #**hdrstop 杂注**  
  
3.  扩展名为 .PCH 的源文件基名称  
  
 有关 /Yc 和 /Yu 的选项，如果这两个编译选项都不也不**hdrstop**杂注指定的文件名，则源文件的基名称用作预编译的头文件的基名称。  
  
 还可以使用预处理命令来执行宏替换，如下所示：  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 以下规则将管理 where **hdrstop**可以放置杂注：  
  
-   它必须出现在任何数据或函数声明/定义的外部。  
  
-   必须在源文件而不是头文件中指定它。  
  
## <a name="example"></a>示例  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 在此示例中， **hdrstop**杂注显示后包含了两个文件和已定义内联函数。 最初，这可能是杂注的临时位置。 但请考虑，使用手动预编译选项 /Yc 和 /Yu 与**hdrstop**杂注使你可以预编译整个源文件-甚至是内联代码。 Microsoft 编译器不会只允许您预编译数据声明。  
  
## <a name="see-also"></a>另请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)