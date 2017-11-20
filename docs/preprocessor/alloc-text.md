---
title: "alloc_text |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs: C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e877f747bc825faac38c3557b52e0f0969257208
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="alloctext"></a>alloc_text
命名指定的函数定义驻留的代码部分。 杂注必须出现在函数声明符和命名函数的函数定义之间。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## <a name="remarks"></a>备注  
 **Alloc_text**杂注不处理 c + + 成员函数或重载的函数。 它是仅适用于带 C 链接声明的函数-也就是说，函数声明与**extern"C"**链接规范。 如果尝试对带 C++ 链接的函数使用此杂注，则会生成编译器错误。  
  
 由于函数寻址使用`__based`不支持，则指定节位置需要使用**alloc_text**杂注。 指定的名称*textsection*应括在双引号中。  
  
 **Alloc_text**杂注必须出现的任何指定函数，并在这些函数的定义之前声明之后。  
  
 中引用的函数**alloc_text**杂注应在杂注相同的模块中定义。 如果未这样做，并且未定义的函数稍后会被编译为其他文本部分，该错误可能会被捕获，也可能不会。 尽管此程序通常都会正常运行，但该函数不会在预期部分中分配。  
  
 在其他的限制**alloc_text**如下所示：  
  
-   它不能在函数内使用。  
  
-   必须在声明函数后且在定义函数前使用它。  
  
## <a name="see-also"></a>另请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)