---
title: 下标
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 2573f30b2dfee20d12afea2a1072bbdcef46228b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231073"
---
# <a name="subscripting"></a>下标

下标运算符（**[]**）（如函数调用运算符）被视为二元运算符。 下标运算符必须是采用单个参数的非静态成员函数。 此自变量可以是任何类型，并指定所需的数组下标。

## <a name="example"></a>示例

下面的示例演示如何创建 **`int`** 实现界限检查的类型向量：

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>注释

当在 `i` 上一个程序中达到10时，**运算符 []** 检测到使用了超出界限的下标并且发出错误消息。

请注意，函数**运算符 []** 返回引用类型。 这会使它成为左值，从而使您可以在赋值运算符的任何一侧使用下标表达式。

## <a name="see-also"></a>另请参阅

[运算符重载](../cpp/operator-overloading.md)
