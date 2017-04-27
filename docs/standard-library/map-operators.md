---
title: "&lt;map&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5721a3bb5c74c6609fd001d5e5759b4f153915d2
ms.lasthandoff: 02/24/2017

---
# <a name="ltmapgt-operators"></a>&lt;map&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
|[operator!= (multimap)](#operator_neq_multimap)|[operator&gt;](#operator_gt_multimap)|[operator&gt;=](#operator_gt__eq_multimap)|  
|[operator&lt;](#operator_lt_multimap)|[operator&lt;=](#operator_lt__eq_multimap)|[operator==](#operator_eq_eq_multimap)|  
  
##  <a name="operator_neq"></a>operator!=  
 测试运算符左侧和右侧的 map 对象是否不相等。  
  
```
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_lt_"></a>operator&lt;  
 测试运算符左侧的映射对象是否小于右侧的映射对象。  
  
```
bool operator<(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_lt__eq"></a>operator&lt;=  
 测试运算符左侧的映射对象是否小于或等于右侧的映射对象。  
  
```
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_eq_eq"></a>operator==  
 测试运算符左侧和右侧的 map 对象是否相等。  
  
```
bool operator==(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_gt_"></a>operator&gt;  
 测试运算符左侧的映射对象是否大于右侧的映射对象。  
  
```
bool operator>(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_gt__eq"></a>operator&gt;=  
 测试运算符左侧的映射对象是否大于或等于右侧的映射对象。  
  
```
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **map** 的对象。  
  
 `right`  
 类型 **map** 的对象。  
  
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
  
##  <a name="operator_neq_multimap"></a>operator!= (multimap)  
 测试运算符左侧和右侧的 multimap 对象是否不相等。  
  
```
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
##  <a name="operator_lt_multimap"></a>operator&lt;  
 测试运算符左侧的 multimap 对象是否小于右侧的 multimap 对象。  
  
```
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
##  <a name="operator_lt__eq_multimap"></a>operator&lt;=  
 测试运算符左侧的 multimap 对象是否小于或等于右侧的 multimap 对象。  
  
```
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
##  <a name="operator_eq_eq_multimap"></a>operator==  
 测试运算符左侧和右侧的 multimap 对象是否相等。  
  
```
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
##  <a name="operator_gt_multimap"></a>operator&gt;  
 测试运算符左侧的 multimap 对象是否大于右侧的 multimap 对象。  
  
```
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
##  <a name="operator_gt__eq_multimap"></a>operator&gt;=  
 测试运算符左侧的 multimap 对象是否大于或等于右侧的 multimap 对象。  
  
```
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multimap` 类型的对象。  
  
 `right`  
 一个 `multimap` 类型的对象。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [\<map>](../standard-library/map.md)




