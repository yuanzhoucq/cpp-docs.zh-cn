---
title: mask_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689405"
---
# <a name="mask_array-class"></a>mask_array 类

一个内部的辅助类模板，它通过提供子集数组之间的操作来支持作为父 valarray 的子集的对象（使用布尔表达式指定）。

## <a name="syntax"></a>语法

## <a name="remarks"></a>备注

此类描述一个对象，该对象存储对类[valarray](../standard-library/valarray-class.md)  **\<Type >** 的对象 `va` 的引用以及类[valarray \<bool >](../standard-library/valarray-bool-class.md)的对象 `ba`，该对象描述要选择的元素的序列。从 `valarray<Type>` 对象。

仅通过编写一个形式为[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)的表达式来构造一个 `mask_array<Type>` 对象。 类 mask_array 的成员函数的行为类似于为 `valarray<Type>` 定义的相应函数签名，只不过只影响选定元素的序列。

序列包含最多 `ba.size` 元素。 仅当 *ba* [ **J**] 为 true，才包括元素 *J*。 因此，序列中的元素数目与 `ba` 中的 true 元素相同。 如果 `I` 是 `ba` 中最低 true 元素的索引，则**va**[`I`] 是所选序列中的元素零。

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

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
