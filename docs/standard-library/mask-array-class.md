---
title: mask_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 9da5e3593288be02819330e11b60e306784054dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460142"
---
# <a name="maskarray-class"></a>mask_array 类

一个内部的辅助模板类，该类通过提供子集阵列之间的操作来支持作为父级 valarray（使用布尔表达式指定）的子集的对象。

## <a name="syntax"></a>语法

## <a name="remarks"></a>备注

此类描述了一个对象, 该对象存储对类`va` [valarray](../standard-library/valarray-class.md) **\<类型**的对象的引用 > 以及`ba`类[\<valarray bool >](../standard-library/valarray-bool-class.md)的对象, 该对象描述要从`valarray<Type>`对象中选择的元素的序列。

只能通过编写`mask_array<Type>`一个形式为[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)的表达式来构造对象。 类 mask_array 的成员函数的行为类似于为定义的`valarray<Type>`对应函数签名, 只不过只影响选定元素的序列。

序列最多`ba.size`包含个元素。 仅当 *ba* [ **J**] 为 true，才包括元素 *J*。 因此, 序列中的元素数量与中`ba`的 true 元素相同。 如果`I`是中`ba`最低 true 元素的索引, 则**va**[ `I`] 在选定序列中为元素零。

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

### <a name="output"></a>Output

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>要求

**标头：** \<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
