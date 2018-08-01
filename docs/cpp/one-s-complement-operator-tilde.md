---
title: '一个&#39;s 二进制求补运算符: ~ |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- "~"
dev_langs:
- C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79d34a4057ccbe5c10a6d22a14eed4317e62c464
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409152"
---
# <a name="one39s-complement-operator-"></a>一个&#39;s 二进制求补运算符: ~
## <a name="syntax"></a>语法  
  
```  
~ cast-expression  
```  
  
## <a name="remarks"></a>备注  
 二进制反码运算符 (`~`)（有时称为“按位反码”运算符）将生成其操作数的按位二进制反码。 即，操作数中为 1 的每个位在结果中为 0。 相反，操作数中为 0 的每个位在结果中为 1。 二进制反码运算符的操作数必须为整型。  
  
## <a name="operator-keyword-for-"></a>~ 的运算符关键字  
 **Compl**运算符是文本等效项`~`。 有两种方法来访问**compl**您的程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md)。  
  
## <a name="example"></a>示例  
  
```cpp 
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 在此示例中，分配给 `y` 的新值是无符号值 0xFFFF 或 0x0000 的二进制反码。  
  
 将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。 请参阅[标准转换](standard-conversions.md)有关如何完成提升的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C++ 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算术运算符](../c-language/unary-arithmetic-operators.md)