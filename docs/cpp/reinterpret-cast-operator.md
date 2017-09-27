---
title: "reinterpret_cast 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- reinterpret_cast
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 71218dc713b24669dc1648b748a0326da0c03152
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="reinterpretcast-operator"></a>reinterpret_cast 运算符
允许将任何指针转换为任何其他指针类型。 也允许将任何整数类型转换为任何指针类型以及反向转换。  
  
## <a name="syntax"></a>语法  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>备注  
 滥用 `reinterpret_cast` 运算符可能很容易带来风险。 除非所需转换本身是低级别的，否则应使用其他强制转换运算符之一。  
  
 `reinterpret_cast` 运算符可用于 `char*` 到 `int*` 或 `One_class*` 到 `Unrelated_class*` 之类的转换，这本身并不安全。  
  
 `reinterpret_cast` 的结果不能安全地用于除强制转换回其原始类型以外的任何用途。 在最好的情况下，其他用途也是不可移植的。  
  
 `reinterpret_cast`运算符不能丢掉**const**， `volatile`，或**__unaligned**属性。 请参阅[const_cast 运算符](../cpp/const-cast-operator.md)有关移除这些特性的信息。  
  
 `reinterpret_cast` 运算符将 null 指针值转换为目标类型的 null 指针值。  
  
 `reinterpret_cast` 的一个实际用途是在哈希函数中，即，通过让两个不同的值几乎不以相同的索引结尾的方式将值映射到索引。  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` 允许将指针视为整数类型。 结果随后将按位移位并与自身进行“异或”运算以生成唯一的索引（具有唯一性的概率非常高）。 该索引随后被标准 C 样式强制转换截断为函数的返回类型。  
  
## <a name="see-also"></a>另请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [关键字](../cpp/keywords-cpp.md)
