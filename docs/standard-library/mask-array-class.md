---
title: mask_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 108c942bef33e44b515d46e953c9d99274e3ce8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475811"
---
# <a name="maskarray-class"></a>mask_array 类

一个内部的辅助模板类，该类通过提供子集阵列之间的操作来支持作为父级 valarray（使用布尔表达式指定）的子集的对象。

## <a name="syntax"></a>语法

## <a name="remarks"></a>备注

此类描述的对象将存储对对象的引用`va`类的[valarray](../standard-library/valarray-class.md)**\<类型 >**，对象及`ba`类的[valarray\<bool >](../standard-library/valarray-bool-class.md)，它描述了要从选择的元素序列`valarray<Type>`对象。

在构造`mask_array<Type>`只通过写入形式的表达式的对象[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)。 Mask_array 类的成员函数，然后就像是为定义的对应函数签名`valarray<Type>`，只不过仅所选元素的序列受到影响。

序列的最多包含`ba.size`元素。 仅当 *ba* [ **J**] 为 true，才包括元素 *J*。 因此，有序列中任意多个元素中，则返回 true 的元素以及`ba`。 如果`I`是中最低 true 元素的索引`ba`，然后**va**[ `I`] 是所选序列中的元素零。

## <a name="example"></a>示例

```cpp
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

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>要求

**标头：**\<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
