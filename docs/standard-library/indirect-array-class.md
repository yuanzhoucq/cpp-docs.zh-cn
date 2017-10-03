---
title: "indirect_array 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray/std::indirect_array
dev_langs:
- C++
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: df1199bd46672b032020d3b463425284f6360298
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="indirectarray-class"></a>indirect_array 类
一个内部的辅助模板类，该类通过提供子集阵列（通过指定父级 valarray 的索引子集进行定义）之间的操作来支持作为 valarray 的子集的对象。  
  
## <a name="syntax"></a>语法  
  
  
  
## <a name="remarks"></a>备注  
 该类描述的对象将存储对 [valarray](../standard-library/valarray-class.md)**\<Type>** 类的 **va** 对象及 **valarray<size_t>** 类的 **xa** 对象的引用，它描述了要从 **valarray\<Type>** 对象中选择的元素序列。  
  
 只可通过编写 **va[xa]** 形式的表达式来构造 **indirect_array\<Type>** 对象。 indirect_array 类的成员函数的行为方式类似于为 **valarray\<Type>** 定义的对应函数签名，只不过仅所选的元素的序列受到影响。  
  
 此序列由 **xa.**[size](../standard-library/valarray-class.md#size) 元素组成，其中元素 `I` 在 **va** 内成为索引 **xa**[ `I`]。  
  
## <a name="example"></a>示例:  
  
```  
// indirect_array.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // Select 2nd, 4th & 6th elements  
   // and assign a value of 10 to them  
   valarray<size_t> indx ( 3 );  
   indx [0] = 2;  
   indx [1] = 4;  
   indx [2] = 6;  
   va[indx] = 10;  
  
   cout << "The modified operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### <a name="output"></a>输出  
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<valarray>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


