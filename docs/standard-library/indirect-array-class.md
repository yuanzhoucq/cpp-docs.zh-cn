---
title: indirect_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687917"
---
# <a name="indirect_array-class"></a>indirect_array 类

一个内部的辅助类模板，它通过在通过指定父级 valarray 的索引子集定义的子集数组间提供操作来支持作为 valarray 子集的对象。

## <a name="syntax"></a>语法

## <a name="remarks"></a>备注

此类描述一个对象，该对象存储对类[valarray](../standard-library/valarray-class.md)  **\<Type >** 的对象 `va`，以及类 `valarray<size_t>` 的对象 `xa`，该类描述要从 `valarray<Type>` 对象中选择的元素的序列。

仅通过编写 `va[xa]` 形式的表达式来构造 `indirect_array<Type>` 的对象。 类 indirect_array 的成员函数的行为类似于为 `valarray<Type>` 定义的相应函数签名，只不过只影响选定元素的序列。

序列由 xa 组成 **。** [size](../standard-library/valarray-class.md#size)元素，其中元素 `I` 成为 `va` 内的索引**xa**[`I`]。

## <a name="example"></a>示例:

```cpp
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

### <a name="output"></a>Output

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>要求

**标头：** \<valarray>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
