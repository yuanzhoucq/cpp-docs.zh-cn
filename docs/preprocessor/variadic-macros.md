---
title: Variadic 宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16549d6b7a80a8aa0f3f98cf9c7cd89c74058959
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540150"
---
# <a name="variadic-macros"></a>Variadic 宏
Variadic 宏是包含数目可变的参数的类似函数的宏。  
  
## <a name="remarks"></a>备注  
 
若要使用可变参数宏，可以将省略号指定为最终形式自变量的宏定义和替换标识符中`__VA_ARGS__`可能定义中使用插入多余的参数。  `__VA_ARGS__` 将替换所有匹配的省略号，包括以逗号分隔的参数。  
  
C 标准，则指定必须将至少一个参数传递给的省略号，以确保该宏无法解析为具有尾随逗号的表达式。  如果为省略号不传递任何参数时，Visual c + + 实现将禁止显示尾随逗号。  
  
## <a name="example"></a>示例  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
    
```Output  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
```  
  
## <a name="see-also"></a>请参阅  
 
[宏 (C/C++)](../preprocessor/macros-c-cpp.md)