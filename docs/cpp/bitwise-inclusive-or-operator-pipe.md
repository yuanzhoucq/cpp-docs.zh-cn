---
title: "按位与或运算符: | |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 792a5ef5576f68925459d8e7a34168afa11871c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-inclusive-or-operator-"></a>按位与或运算符：|
## <a name="syntax"></a>语法  
  
```  
  
expression   
|  
 expression  
  
```  
  
## <a name="remarks"></a>备注  
 非独占的按位或运算符 (**&#124;**) 将每个位与第一个操作数与其第二操作数的相应位进行比较。 如果其中一个位是 1，则将对应的结果位设置为 1。 否则，将对应的结果位设置为 0。  
  
 按位“与或”运算符的两个操作数必须为整型。 中涵盖的常用算术转换[标准转换](standard-conversions.md)适用于操作数。  
  
## <a name="operator-keyword-for-124"></a>运算符关键字 &#124;  
 `bitor`运算符是文本等效项**&#124;**。 有两种方法来访问`bitor`在程序中的运算符： 包含头文件`iso646.h`，或使用编译[/Za](../build/reference/za-ze-disable-language-extensions.md) （禁用语言扩展） 编译器选项。  
  
## <a name="example"></a>示例  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [C + + 内置运算符、 优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 按位运算符](../c-language/c-bitwise-operators.md)

