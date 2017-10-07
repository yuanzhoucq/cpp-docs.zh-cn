---
title: "一个 &#39; s 求补运算符: ~ |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ~
dev_langs:
- C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 918555af04d20be2533b488ee26f031e10a54ca4
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="one39s-complement-operator-"></a>一个 &#39; s 求补运算符: ~
## <a name="syntax"></a>语法  
  
```  
  
~ cast-expression  
```  
  
## <a name="remarks"></a>备注  
 二进制反码运算符 (`~`)（有时称为“按位反码”运算符）将生成其操作数的按位二进制反码。 即，操作数中为 1 的每个位在结果中为 0。 相反，操作数中为 0 的每个位在结果中为 1。 二进制反码运算符的操作数必须为整型。  
  
## <a name="operator-keyword-for-"></a>~ 的运算符关键字  
 `compl` 运算符是 `~` 的文本等效项。 有两种方法来访问`compl`在程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md)。  
  
## <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算术运算符](../c-language/unary-arithmetic-operators.md)
