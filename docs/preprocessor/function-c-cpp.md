---
title: 函数杂注
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: f99f3c878789a6c47fdb0d48e0a8690d65fa8062
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220137"
---
# <a name="function-pragma"></a>函数杂注

通知编译器生成对杂注的参数列表中指定的函数的调用, 而不是内联它们。

## <a name="syntax"></a>语法

> **#pragma 函数 (** *function1* [ **,** *function2* ...] **)**

## <a name="remarks"></a>备注

内部函数通常生成为内联代码, 而不是函数调用。 如果使用[内部杂注](intrinsic.md)或[/Oi](../build/reference/oi-generate-intrinsic-functions.md)编译器选项告知编译器生成内部函数, 则可以使用**函数**杂注显式强制执行函数调用。 出现**函数**杂注后, 它将在包含指定的内部函数的第一个函数定义处生效。 该效果将继续到源文件的末尾, 或指定相同内部函数的`intrinsic`杂注的外观。 在全局级别, 只能在函数之外使用**函数**杂注。

有关具有内部形式的函数的列表, 请参阅[内部杂注](intrinsic.md)。

## <a name="example"></a>示例

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
