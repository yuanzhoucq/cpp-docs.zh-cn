---
title: indirect_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 43c54bf3dae02eb117b15cae0dd7de9bb4a9db51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448875"
---
# <a name="indirectarray-class"></a>indirect_array 类

一个内部的辅助模板类，该类通过提供子集阵列（通过指定父级 valarray 的索引子集进行定义）之间的操作来支持作为 valarray 的子集的对象。

## <a name="syntax"></a>语法

## <a name="remarks"></a>备注

此类描述的对象将存储对对象的引用`va`类的[valarray](../standard-library/valarray-class.md)**\<类型 >**，对象及`xa`类的`valarray<size_t>`，它描述了要从选择的元素序列`valarray<Type>`对象。

在构造`indirect_array<Type>`只通过写入形式的表达式的对象`va[xa]`。 Indirect_array 类的成员函数，然后就像是为定义的对应函数签名`valarray<Type>`，只不过仅所选元素的序列受到影响。

序列组成**xa。**[大小](../standard-library/valarray-class.md#size)元素，其中元素`I`成为索引**xa**[ `I`] 内`va`。

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

### <a name="output"></a>输出

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>要求

**标头：**\<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
