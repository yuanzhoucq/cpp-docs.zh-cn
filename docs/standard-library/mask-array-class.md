---
title: "mask_array 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray/std::mask_array
dev_langs:
- C++
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 882091956f9d9c5985e3bfacfe015ff81e84ac6c
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="maskarray-class"></a>mask_array 类
一个内部的辅助模板类，该类通过提供子集阵列之间的操作来支持作为父级 valarray（使用布尔表达式指定）的子集的对象。  
  
## <a name="syntax"></a>语法  
  
  
  
## <a name="remarks"></a>备注  
 该类描述的对象将存储对 [valarray](../standard-library/valarray-class.md)**\<Type>** 类的 **va** 对象及 [valarray\<bool>](../standard-library/valarray-bool-class.md) 类的 **ba** 对象的引用，它描述了要从 **valarray\<Type>** 对象中选择的元素序列。  
  
 只通过写入 [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at) 形式的表达式即可构造 **mask_array\<Type>** 对象。 然后 mask_array 类的成员函数的行为方式就类似于为 **valarray\<Type>** 定义的对应的函数签名，只不过仅所选的元素的序列受到影响。  
  
 该序列大部分由 **ba.size** 元素组成。 仅当 *ba* [ **J**] 为 true，才包括元素 *J*。 因此 **ba**中有多少 true 元素序列中就有多少元素。 如果 `I` 是 **ba**中最低 true 元素的索引，那么 **va**[ `I`] 则是所选序列中的元素零。  
  
## <a name="example"></a>示例:  
  
```  
// mask_array.cpp  
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
  
   // Use masked subsets to assign a value of 10  
   // to all elements grrater than 3 in value  
   va [va > 3 ] = 10;  
   cout << "The modified operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### <a name="output"></a>输出  
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<valarray>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


