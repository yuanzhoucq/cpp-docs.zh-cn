---
title: "C 注释 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f8281cce930a9f1b98536b65762bf8b940b0d973
ms.lasthandoff: 02/24/2017

---
# <a name="c-comments"></a>C 注释
“注释”是一个以正斜杠/星号组合（<b>/\*</b>）开头的字符序列，编译器会将正斜杠/星号组合视为单个空白字符，要不然就忽略它。 注释可以包含可表示字符集中的任意字符组合，包括换行符，但“结束注释”分隔符 (<b>\*/</b>) 除外。 注释可以占用多行，但无法嵌套。  
  
 注释可以出现在允许使用空白字符的任何地方。 由于编译器将注释视为空白字符，因此不能将注释包含在标记中。 编译器将忽略注释中的字符。  
  
 使用注释来记录您的代码。 本示例是编译器接受的注释：  
  
```  
/* Comments can contain keywords such as  
   for and while without generating errors. */  
```  
  
 注释可以与代码语句出现在同一行中：  
  
```  
printf( "Hello\n" );  /* Comments can go here */  
```  
  
 可以选择在函数或程序模块前面放置一个描述性注释块：  
  
```  
/* MATHERR.C illustrates writing an error routine   
 * for math functions.   
 */   
```  
  
 由于注释不能包含嵌套注释，因此本示例导致了一个错误：  
  
```  
/* Comment out this routine for testing   
  
   /* Open file */  
    fh = _open( "myfile.c", _O_RDONLY );  
    .  
    .  
    .  
 */  
```  
  
 该错误发生的原因是编译器将单词 `*/` 后的第一个 `Open file` 识别为注释的末尾。 编译器尝试处理剩余的文本，当它在注释外找到 `*/` 时，便产生了错误。  
  
 尽管您可以出于测试目的使用注释来呈现某些处于非活动状态的代码行，但预处理器指令 `#if` 和 `#endif` 以及条件编译都是执行此任务的有用的替代选择。 有关详细信息，请参阅预处理器参考中的[预处理器指令](../preprocessor/preprocessor-directives.md)。  
  
 **Microsoft 专用**  
  
 Microsoft 编译器还支持前面有两个正斜杠 (**//**) 的单行注释。 如果使用 /Za（ANSI 标准）进行编译，这些注释将产生错误。 这些注释不能扩展到第二行。  
  
```  
// This is a valid comment  
```  
  
 以两个正斜杠 (**//**) 开头的注释被前面没有转义字符的下一个换行符终止。 在下一个示例中，换行符的前面有一个反斜杠 (**\\**)，这将创建“转义序列”。 此转义序列会使编译器将下一行视为上一行的一部分。 （有关详细信息，请参阅[转义序列](../c-language/escape-sequences.md)。）  
  
```  
// my comment \  
    i++;   
```  
  
 因此，`i++;` 语句被注释掉。  
  
 Microsoft C 的默认设置是启用 Microsoft 扩展。 请使用 /Za 禁用这些扩展。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [C 标记](../c-language/c-tokens.md)

