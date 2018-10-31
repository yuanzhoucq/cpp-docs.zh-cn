---
title: binder1st 类
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: a8e962e118d162e46e2edfca3ce11e7cbf322e10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439625"
---
# <a name="binder1st-class"></a>binder1st 类

一种模板类，用于提供构造函数，通过将二元函数的第一个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。

## <a name="syntax"></a>语法

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& Func,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>参数

*Func*<br/>
要转换为一元函数对象的二元函数对象。

*left*<br/>
要将二元函数对象的第一个参数绑定到的值。

*right*<br/>
改编的二元对象将其与第二个参数进行比较的参数值。

## <a name="return-value"></a>返回值

将二元函数对象的第一个参数绑定到值而得出的一元函数对象*左*。

## <a name="remarks"></a>备注

此模板类存储二元函数对象的副本*Func*中`op`，以及一份*左*中`value`。 它将其成员函数 `operator()` 定义为返回 **op**( **value**, `right`)。

如果*Func*是类型的对象`Operation`并`c`是常量，则[bind1st](../standard-library/functional-functions.md#bind1st) ( `Func`， `c` ) 等效于`binder1st`类构造函数`binder1st` \< **操作**> ( `Func`， `c` ) 且更为方便。

## <a name="example"></a>示例

```cpp
// functional_binder1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
/* Output:
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
*/
```

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
