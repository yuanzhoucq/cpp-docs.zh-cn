---
title: "__unaligned |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: 11
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9f899add9a1306344a10840220f3b7504e917d91
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="unaligned"></a>__unaligned
声明带有 `__unaligned` 修饰符的指针时，编译器将假定该指针处理未对齐的数据。 因此，对于面向 Itanium Processor Family (IPF) 计算机的应用程序，编译器将生成逐个字节地读取未对齐数据的代码。  
  
## <a name="remarks"></a>备注  
 `__unaligned`修饰符可用于[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]和[!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)]编译器但只有会影响面向 IPF 计算机的应用。 此修饰符只描述已处理数据的对齐；指针本身被假定为已对齐。  
  
 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)]处理器生成对齐错误时它访问未对齐的数据，并处理故障的时间会降低性能。 使用 `__unaligned` 修饰符可以让处理器逐个字节地读取数据并避免错误。 此修饰符不需要[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]应用程序由于[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]处理器处理未对齐的数据，而不会出错。  
  
 有关对齐的详细信息，请参阅：  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__alignof 运算符](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)  
  
-   [结构对齐示例](../build/examples-of-structure-alignment.md)  
  
## <a name="example"></a>示例  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
