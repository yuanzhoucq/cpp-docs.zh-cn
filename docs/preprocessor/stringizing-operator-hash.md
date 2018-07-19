---
title: 字符串化运算符 （#） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7891b03fe80b5ad91ad52cf4577d237350d4584c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841694"
---
# <a name="stringizing-operator-"></a>字符串化运算符 (#)
数字符号或"字符串化"运算符 (**#**) 将宏参数转换为字符串，而不扩展参数定义。 它只用于采用自变量的宏。 如果它在宏定义中位于形参之前，则由宏调用传递的实参将用引号引起来并被视为字符串。 字符串随后替换宏定义中的字符串化运算符和形参的组合的每个匹配项。  
  
> [!NOTE]
>  不再支持对 ANSI C 标准的 Microsoft C（6.0 版和早期版本）扩展，该扩展之前扩展了出现在字符串和字符常量内的扩展的宏形式自变量。 应使用字符串化重新编写依赖此扩展的代码 (**#**) 运算符。  
  
在自变量的第一个标记前且紧跟自变量的最后一个标记的空格将被忽略。 在生成的字符串中，将自变量标记之间的所有空格减少到单一空格。 因此，如果注释出现在实参的两个标记之间，则将其减少为单个空格。 生成的字符串自动与仅由空格分隔的任何相邻的字符串连接。  
  
此外，如果自变量中通常包含的字符需要转义序列在字符串中使用时 (例如，在引号 (**"**) 或反斜杠 (**\\**) 字符)，则必要的转义反斜杠会自动插入该字符前面。  
  
Visual c + + 字符串化运算符用于包含转义序列的字符串时其行为不会不正确。 在此情况下，编译器将生成[编译器错误 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)。  
  
## <a name="example"></a>示例  
以下示例显示一个包含字符串化运算符的宏定义和一个调用该宏的主函数：  
  
在预处理期间将扩展此类调用，并将生成以下代码：  
  
```cpp  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```cpp  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
```Output  
In quotes in the printf function call  
"In quotes when printed to the screen"  
"This: \"  prints an escaped double quote"  
```  
  
## <a name="example"></a>示例  
以下示例说明如何扩展宏参数：  
  
```cpp  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## <a name="see-also"></a>请参阅  
 [预处理器运算符](../preprocessor/preprocessor-operators.md)