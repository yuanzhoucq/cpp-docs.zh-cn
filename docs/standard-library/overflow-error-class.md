---
title: overflow_error 类
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::overflow_error
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
ms.openlocfilehash: b1faad62dc8e564d97170b5244b6406ae8e1dee6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450140"
---
# <a name="overflowerror-class"></a>overflow_error 类

此类用作引发报告算数溢出的所有异常的基类。

## <a name="syntax"></a>语法

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>备注

[what](../standard-library/exception-class.md) 返回的值是 **message**`.`[data](../standard-library/basic-string-class.md#data) 的副本。

## <a name="example"></a>示例

```cpp
// overflow_error.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 33 > bitset;
      bitset[32] = 1;
      bitset[0] = 1;
      unsigned long x = bitset.to_ulong( );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bitset<N> overflow
Type class std::overflow_error
*/
```

## <a name="requirements"></a>要求

**标头：** \<stdexcept>

**命名空间：** std

## <a name="see-also"></a>请参阅

[runtime_error 类](../standard-library/runtime-error-class.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
