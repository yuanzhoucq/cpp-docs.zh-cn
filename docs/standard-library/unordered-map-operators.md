---
title: '&lt;unordered_map&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: fe4877bc5b371a2570c18950bac36a003078ccc7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78873948"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt; 运算符

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  operator!=

测试位于运算符左侧的 [unordered_map](../standard-library/unordered-map-class.md) 对象是否与位于右侧的 unordered_map 对象不相等。

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>参数

*左*\
一个 `unordered_map` 类型的对象。

*right*\
一个 `unordered_map` 类型的对象。

### <a name="return-value"></a>返回值

如果 unordered_maps 不相等，则**为 true** ;如果相等，则**为 false** 。

### <a name="remarks"></a>备注

在其中存储元素的二元顺序不会影响 unordered_map 对象之间的比较。 如果两个 unordered_map 具有相同的元素数，并且一个容器中的元素是另一个容器中的元素的排列，则这两个 unordered_map 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**输出：**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>operator==

测试位于运算符左侧的 [unordered_map](../standard-library/unordered-map-class.md) 对象是否与位于右侧的 unordered_map 对象相等。

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>参数

*左*\
一个 `unordered_map` 类型的对象。

*right*\
一个 `unordered_map` 类型的对象。

### <a name="return-value"></a>返回值

如果 unordered_maps 相等，则为**true** ;如果不相等，则**为 false** 。

### <a name="remarks"></a>备注

在其中存储元素的二元顺序不会影响 unordered_map 对象之间的比较。 如果两个 unordered_map 具有相同的元素数，并且一个容器中的元素是另一个容器中的元素的排列，则这两个 unordered_map 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**输出：**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>  operator!=

测试位于运算符左侧的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 对象是否与位于右侧的 unordered_multimap 对象不相等。

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>参数

*左*\
一个 `unordered_multimap` 类型的对象。

*right*\
一个 `unordered_multimap` 类型的对象。

### <a name="return-value"></a>返回值

如果 unordered_multimaps 不相等，则**为 true** ;如果相等，则**为 false** 。

### <a name="remarks"></a>备注

在其中存储元素的二元顺序不会影响 unordered_multimap 对象之间的比较。 如果两个 unordered_multimap 具有相同的元素数，并且一个容器中的元素是另一个容器中的元素的排列，则这两个 unordered_multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**输出：**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>operator==

测试位于运算符左侧的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 对象是否与位于右侧的 unordered_multimap 对象相等。

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>参数

*左*\
一个 `unordered_multimap` 类型的对象。

*right*\
一个 `unordered_multimap` 类型的对象。

### <a name="return-value"></a>返回值

如果 unordered_multimaps 相等，则为**true** ;如果不相等，则**为 false** 。

### <a name="remarks"></a>备注

在其中存储元素的二元顺序不会影响 unordered_multimap 对象之间的比较。 如果两个 unordered_multimap 具有相同的元素数，并且一个容器中的元素是另一个容器中的元素的排列，则这两个 unordered_multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**输出：**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>另请参阅

[<unordered_map>](../standard-library/unordered-map.md)
