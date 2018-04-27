---
title: '&lt;map&gt; 运算符 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
dev_langs:
- C++
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 623be5ce3a0492db98f1375746446a3d9f97f7d9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltmapgt-operators"></a>&lt;map&gt; 运算符

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|
|[operator!= (multimap)](#op_neq_multimap)|[operator&gt;](#op_gt_multimap)|[operator&gt;=](#op_gt_eq_multimap)|
|[operator&lt;](#op_lt_multimap)|[operator&lt;=](#op_lt_eq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>operator!=

测试运算符左侧和右侧的 map 对象是否不相等。

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果 map 不相等，则为 **true**；如果 map 相等，则为 **false**。

### <a name="remarks"></a>备注

映射对象之间的比较基于其元素的成对比较。 如果两个映射具有的元素数目相等且对应元素具有相同的值，则两个映射相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_lt"></a>operator&lt;

测试运算符左侧的映射对象是否小于右侧的映射对象。

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果运算符左侧的映射严格小于运算符右侧的映射，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

映射对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
\* Output:
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
*\
```

## <a name="op_lt_eq"></a>  operator&lt;=

测试运算符左侧的映射对象是否小于或等于右侧的映射对象。

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果运算符左侧的映射小于或等于右侧的映射，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
\* Output:
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
*\
```

## <a name="op_eq_eq"></a>operator==

测试运算符左侧和右侧的 map 对象是否相等。

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果运算符左侧的映射等于运算符右侧的映射，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

映射对象之间的比较基于其元素的成对比较。 如果两个映射具有的元素数目相等且对应元素具有相同的值，则两个映射相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_gt"></a>operator&gt;

测试运算符左侧的映射对象是否大于右侧的映射对象。

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果运算符左侧的映射大于右侧的映射，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

映射对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
\* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*\
```

## <a name="op_gt_eq"></a>  operator&gt;=

测试运算符左侧的映射对象是否大于或等于右侧的映射对象。

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象**映射**。

`right` 类型的对象**映射**。

### <a name="return-value"></a>返回值

如果运算符左侧的映射大于或等于列表右侧的映射，则为 **true**，否则为 **false**。

### <a name="example"></a>示例

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
\* Output:
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
*\
```

## <a name="op_neq_multimap"></a>operator!= (multimap)

测试运算符左侧和右侧的 multimap 对象是否不相等。

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果 multimap 不相等，则为 **true**；如果 multimap 相等，则为 **false**。

### <a name="remarks"></a>备注

multimap 对象之间的比较基于其元素的成对比较。 如果两个 multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
\* Output:
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
*\
```

## <a name="op_lt_multimap"></a>operator&lt;

测试运算符左侧的 multimap 对象是否小于右侧的 multimap 对象。

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的多重映射严格小于右侧的多重映射，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

multimap 对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
*\
```

## <a name="eq_multimap"></a>  operator&lt;=

测试运算符左侧的 multimap 对象是否小于或等于右侧的 multimap 对象。

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的多重映射小于或等于右侧的多重映射，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
\* Output:
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
*\
```

## <a name="op_eq_eq_multimap"></a>operator==

测试运算符左侧和右侧的 multimap 对象是否相等。

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的多重映射等于右侧的多重映射，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

multimap 对象之间的比较基于其元素的成对比较。 如果两个 multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
\* Output:
m1 and m2 are not equal
m1 and m3 are equal
*\
```

## <a name="op_gt_multimap"></a>operator&gt;

测试运算符左侧的 multimap 对象是否大于右侧的 multimap 对象。

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的多重映射大于右侧的多重映射，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

multimap 对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
\* Output:
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
*\
```

## <a name="op_gt_eq_multimap"></a>  operator&gt;=

测试运算符左侧的 multimap 对象是否大于或等于右侧的 multimap 对象。

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`multimap`。

`right` 类型的对象`multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的多重映射大于或等于列表右侧的多重映射，则为 **true**，否则为 **false**。

### <a name="example"></a>示例

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
*\
```

## <a name="see-also"></a>请参阅

[\<map>](../standard-library/map.md)<br/>
