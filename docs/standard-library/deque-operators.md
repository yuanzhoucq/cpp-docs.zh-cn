---
title: '&lt;deque&gt; 运算符 | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
dev_langs:
- C++
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 5055d637e385754e0cd2c7cf46402bdf6d53b3a4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314503"
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; 运算符

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>operator!=

测试运算符左侧的 deque 对象是否不等于右侧的 deque 对象。

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果 deque 对象不相等，则为 **true**；如果 deque 对象相等，则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 如果两个 deque 对象具有的元素数量相等且对应元素具有相同的值，则两个列表相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
/* Output:
The deques are not equal.
*/
```

## <a name="op_lt"></a>operator&lt;

测试运算符左侧的 deque 对象是否小于右侧的 deque 对象。

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 deque 小于且不等于运算符右侧的 deque，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
/* Output:
Deque c1 is less than deque c2.
*/
```

## <a name="op_lt_eq"></a>  operator&lt;=

测试运算符左侧的 deque 对象是否小于或等于右侧的 deque 对象。

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 deque 小于或等于右侧的 deque，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 两个对象之间的小于或等于关系基于首对不相等元素的比较。

### <a name="example"></a>示例

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
/* Output:
Deque c1 is less than or equal to deque c2.
*/

```

## <a name="op_eq_eq"></a>operator==

测试运算符左侧的 deque 对象是否等于右侧的 deque 对象。

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 deque 等于运算符右侧的 deque，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 如果两个 deque 具有的元素数量相等且对应元素具有相同的值，则两个列表相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
/* Output:
The deques are equal.
The deques are not equal.
*/

```

## <a name="op_gt"></a>operator&gt;

测试运算符左侧的 deque 对象是否大于右侧的 deque 对象。

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 deque 大于运算符右侧的 deque，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
/* Output:
Deque c1 is greater than deque c2.
*/

```

## <a name="op_gt_eq"></a>  operator&gt;=

测试运算符左侧的 deque 对象是否大于或等于右侧的 deque 对象。

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
一个 `deque` 类型的对象。

*right*<br/>
一个 `deque` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的 deque 大于或等于右侧的 deque，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

deque 对象之间的比较基于其元素的成对比较。 两个对象之间大于或等于的关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
/* Output:
Deque c1 is greater than or equal to deque c2.
*/
```

## <a name="see-also"></a>请参阅

[\<deque>](../standard-library/deque.md)<br/>
