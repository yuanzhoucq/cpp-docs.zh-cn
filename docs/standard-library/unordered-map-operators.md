---
title: "&lt;unordered_map&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs: C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
caps.latest.revision: "7"
manager: ghogen
ms.openlocfilehash: 9825a0073355700edbe1906e8b2cad4535085bf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map&gt; 运算符
|||||  
|-|-|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|  
  
##  <a name="op_neq"></a>operator!=  
 测试位于运算符左侧的 [unordered_map](../standard-library/unordered-map-class.md) 对象是否与位于右侧的 unordered_map 对象不相等。  
  
```
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `unordered_map` 类型的对象。  
  
 `right`  
 一个 `unordered_map` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 unordered_map 不相等，则为 `true`；如果它们相等，则为 `false`。  
  
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
  
##  <a name="op_eq_eq"></a>operator==  
 测试位于运算符左侧的 [unordered_map](../standard-library/unordered-map-class.md) 对象是否与位于右侧的 unordered_map 对象相等。  
  
```
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `unordered_map` 类型的对象。  
  
 `right`  
 一个 `unordered_map` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 unordered_map 相等，则为 `true`；如果它们不相等，则为 `false`。  
  
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
  
##  <a name="op_neq_multimap"></a>operator!=  
 测试位于运算符左侧的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 对象是否与位于右侧的 unordered_multimap 对象不相等。  
  
```
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `unordered_multimap` 类型的对象。  
  
 `right`  
 一个 `unordered_multimap` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 unordered_multimap 不相等，则为 `true`；如果它们相等，则为 `false`。  
  
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
  
##  <a name="op_eq_eq_multimap"></a>operator==  
 测试位于运算符左侧的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 对象是否与位于右侧的 unordered_multimap 对象相等。  
  
```
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `unordered_multimap` 类型的对象。  
  
 `right`  
 一个 `unordered_multimap` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 unordered_multimap 相等，则为 `true`；如果它们不相等，则为 `false`。  
  
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



