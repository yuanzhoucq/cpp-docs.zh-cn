---
title: '&lt;set&gt; 运算符'
ms.date: 03/27/2019
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: a3256b7d963feca75e4a975def0f6da77538d278
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217501"
---
# <a name="ltsetgt-operators"></a>&lt;set&gt; 运算符

## <a name="operator-set"></a><a name="op_neq"></a>operator！ = （set）

测试运算符左侧的 set 对象是否不等于右侧的 set 对象。

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果这些集不相等，则为;**`false`** 如果集相等，则为。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 如果两个集具有的元素数目相等且对应元素的值相同，则两个集相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="operatorlt-set"></a><a name="op_lt"></a>运算符 &lt; （set）

测试运算符左侧的集对象是否小于右侧的集对象。

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的集严格小于运算符右侧的集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="operatorlt-set"></a><a name="op_lt_eq"></a>operator &lt; = （set）

测试运算符左侧的集对象是否小于或等于右侧的集对象。

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的集小于或等于运算符右侧的集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 两个对象之间的小于或等于关系基于首对不相等元素的比较。

### <a name="example"></a>示例

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
```

```Output
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
```

## <a name="operator-set"></a><a name="op_eq_eq"></a>operator = = （set）

测试运算符左侧的 set 对象是否等于右侧的 set 对象。

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的集等于运算符右侧的集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 如果两个集具有的元素数目相等且对应元素的值相同，则两个集相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
```

```Output
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
```

## <a name="operatorgt-set"></a><a name="op_gt"></a>运算符 &gt; （set）

测试运算符左侧的集对象是否大于右侧的集对象。

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的集大于运算符右侧的集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="operatorgt-set"></a><a name="op_gt_eq"></a>operator &gt; = （set）

测试运算符左侧的集对象是否大于或等于右侧的集对象。

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `set` 类型的对象。

*然后*\
一个 `set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的集大于或等于列表右侧的集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

集对象之间的比较基于其元素的成对比较。 两个对象之间大于或等于的关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
```

```Output
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
```

## <a name="operator-multiset"></a><a name="op_neq_multiset"></a>operator！ = （多重集）

测试运算符左侧的 multiset 对象是否不等于右侧的 multiset 对象。

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果集或多重集不相等，则为;**`false`** 如果集或多重集相等，则为。

### <a name="remarks"></a>备注

多重集对象之间的比较基于其元素的成对比较。 如果两个集或多重集具有的元素数目相等且对应元素具有相同的值，则这两个集或多重集相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="operatorlt-multiset"></a><a name="op_lt_multiset"></a>运算符 &lt; （多重集）

测试运算符左侧的多重集对象是否小于右侧的多重集对象。

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的多重集严格小于运算符右侧的多重集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

多重对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
```

## <a name="operatorlt-multiset"></a><a name="op_lt_eq_multiset"></a>operator &lt; = （多重集）

测试运算符左侧的多重集对象是否小于或等于右侧的多重集对象。

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的多重集小于或等于运算符右侧的多重集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

多重对象之间的比较基于其元素的成对比较。 两个对象之间的小于或等于关系基于首对不相等元素的比较。

### <a name="example"></a>示例

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
```

## <a name="operator-multiset"></a><a name="op_eq_eq_multiset"></a>operator = = （多重集）

测试运算符左侧的 multiset 对象是否等于右侧的 multiset 对象。

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的多重集等于运算符右侧的多重集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

多重对象之间的比较基于其元素的成对比较。 如果两个集或多重集具有的元素数目相等且对应元素具有相同的值，则这两个集或多重集相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="operatorgt-multiset"></a><a name="op_gt_multiset"></a>运算符 &gt; （多重集）

测试运算符左侧的多重集对象是否大于右侧的多重集对象。

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的多重集大于运算符右侧的多重集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

多重对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
```

## <a name="operatorgt-multiset"></a><a name="op_gt_eq_multiset"></a>operator &gt; = （多重集）

测试运算符左侧的多重集对象是否大于或等于右侧的多重集对象。

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
一个 `multiset` 类型的对象。

*然后*\
一个 `multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的多重集大于或等于列表右侧的多重集，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

多重对象之间的比较基于其元素的成对比较。 两个对象之间大于或等于的关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
```
