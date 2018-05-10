---
title: '&lt;hash_map&gt; 运算符 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: aa5c2a662fb5e827978a7c00aa3035dcc6cc97f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map&gt; 运算符

|||
|-|-|
|[operator!=](#op_neq)|[operator!= (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>operator!=

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_map 类](unordered-map-class.md)。

测试运算符左侧的 hash_map 对象是否不等于右侧的 hash_map 对象。

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`hash_map`。

`right` 类型的对象`hash_map`。

### <a name="return-value"></a>返回值

如果 hash_map 不相等，则为 **true**；如果 hash_map 相等，则为 **false**。

### <a name="remarks"></a>备注

hash_map 对象之间的比较基于其元素的成对比较。 如果两个 hash_map 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_map 相等。 否则，它们不相等。

成员[< hash_map >](hash-map.md)和[< hash_set >](hash-set.md)标头文件中[stdext Namespace](stdext-namespace.md)。

### <a name="example"></a>示例

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="op_eq_eq"></a>operator==

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_map 类](unordered-map-class.md)。

测试运算符左侧的 hash_map 对象是否等于右侧的 hash_map 对象。

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`hash_map`。

`right` 类型的对象`hash_map`。

### <a name="return-value"></a>返回值

如果运算符左侧的 hash_map 等于运算符右侧的 hash_map，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

hash_map 对象之间的比较基于其元素的成对比较。 如果两个 hash_map 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_map 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="op_neq_mm"></a>  运算符 ！ = (hash_multimap)

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multimap 类](unordered-multimap-class.md)。

测试运算符左侧的 hash_multimap 对象是否不等于右侧的 hash_multimap 对象。

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`hash_multimap`。

`right` 类型的对象`hash_multimap`。

### <a name="return-value"></a>返回值

如果 hash_multimap 不相等，则为 **true**；如果 hash_multimap 相等，则为 **false**。

### <a name="remarks"></a>备注

hash_multimap 对象之间的比较基于其元素的成对比较。 如果两个 hash_multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="op_eq_eq_mm"></a>  运算符 = = (hash_multimap)

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_multimap 类](unordered-multimap-class.md)。

测试运算符左侧的 hash_multimap 对象是否等于右侧的 hash_multimap 对象。

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

`left` 类型的对象`hash_multimap`。

`right` 类型的对象`hash_multimap`。

### <a name="return-value"></a>返回值

如果运算符左侧的 hash_multimap 等于运算符右侧的 hash_multimap，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

hash_multimap 对象之间的比较基于其元素的成对比较。 如果两个 hash_multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multimap 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>请参阅

[<hash_map>](hash-map.md)<br/>
