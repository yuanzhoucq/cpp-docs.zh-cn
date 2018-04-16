---
title: "令牌 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 852165a345b36c2ea07d18334b050d5fcb8f7bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tokens-c"></a>令牌 （c + +）
标记是对编译器有用的 C++ 程序的最小元素。 C++ 分析器识别以下类型的标记：标识符、关键字、文本、运算符、标点和其他分隔符。 这些标记流构成一个翻译单元。  
  
 标记通常由 *空格*分隔。 可以有一个或多个空格：  
  
-   空白  
  
-   水平或垂直制表符  
  
-   新行  
  
-   换页  
  
-   注释  
  
 分析器可识别关键字、标识符、文本、运算符和标点符号。 有关特定标记类型的信息，请参阅 [关键字](../cpp/keywords-cpp.md)、 [标识符](../cpp/identifiers-cpp.md)、 [数字、布尔值和指针文本](../cpp/numeric-boolean-and-pointer-literals-cpp.md)、 [字符串和字符文本](../cpp/string-and-character-literals-cpp.md)、 [用户定义的文本](../cpp/user-defined-literals-cpp.md)、 [C++ 内置运算符、优先级和结合性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)以及 [标点符号](../cpp/punctuators-cpp.md)。 除根据需要用于分隔标记外，空格将被忽略。  
  
 预处理标记在预处理阶段用于生成流传输到编译器的令牌。 预处理令牌的类别有标头名称、标识符、预处理数字、字符文本、字符串文本、预处理运算符和标点符号，以及与其他类别均不符的单个非空白字符。 字符和字符串文本可以是用户定义的文本。 预处理标记可以由空格或注释分隔。  
  
 分析器将标记与输入流区分开，方法是在从左到右的扫描中使用输入字符来创建尽可能最长的标记。 考虑此代码片段：  
  
```  
a = i+++j;  
```  
  
 编写代码的程序员可能已考虑以下两个语句之一：  
  
```  
a = i + (++j)  
  
a = (i++) + j  
```  
  
 由于分析器将从输入流创建尽可能长的标记，因此会选择第二个说明，创建标记 `i++`、 `+`和 `j`。  
  
## <a name="see-also"></a>请参阅  
 [词法约定](../cpp/lexical-conventions.md)