---
title: "&lt;set&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
caps.latest.revision: 8
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 3ce8af6d17082b8838b01a9121e91d3ee23f90d4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltsetgt-operators"></a>&lt;set&gt; 运算符
||||  
|-|-|-|  
|[operator!= (set)](#op_neq)|[operator&gt; (set)](#op_gt)|[operator&gt;= (set)](#eq)|  
|[operator&lt; (set)](#op_lt)|[operator&lt;= (set)](#eq)|[operator== (set)](#op_eq_eq)|  
|[operator!= (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|  
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|  
  
##  <a name="op_neq"></a>operator!= (set)  
 测试运算符左侧的 set 对象是否不等于右侧的 set 对象。  
  
```
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果集不相等，则为 **true**；如果集相等，则为 **false**。  
  
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
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_lt"></a>operator&lt; (set)  
 测试运算符左侧的集对象是否小于右侧的集对象。  
  
```
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的集严格大于右侧的集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
The set s1 is less than the set s2.  
The set s1 is not less than the set s3.  
*\  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;= (set)  
 测试运算符左侧的集对象是否小于或等于右侧的集对象。  
  
```
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的集小于或等于右侧的集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
Set s1 is less than or equal to the set s2.  
The set s1 is greater than the set s3.  
Set s1 is less than or equal to the set s4.  
*\  
```  
  
##  <a name="op_eq_eq"></a>operator== (set)  
 测试运算符左侧的 set 对象是否等于右侧的 set 对象。  
  
```
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的集等于运算符右侧的集，则为 **true**，否则为 **false**。  
  
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
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_gt"></a>operator&gt; (set)  
 测试运算符左侧的集对象是否大于右侧的集对象。  
  
```
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的集大于右侧的集，则为 **true**，否则为 **false**。  
  
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
\* Output:   
The set s1 is not greater than the set s2.  
The set s1 is greater than the set s3.  
*\  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;= (set)  
 测试运算符左侧的集对象是否大于或等于右侧的集对象。  
  
```
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 **set** 类型的对象。  
  
 `right`  
 一个 **set** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的集大于或等于列表右侧的集，则为 **true**，否则为 **false**。  
  
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
\* Output:   
The set s1 is less than the set s2.  
Set s1 is greater than or equal to set s3.  
Set s1 is greater than or equal to set s4.  
*\  
```  
  
##  <a name="op_neq_multiset"></a>operator!= (multiset)  
 测试运算符左侧的 multiset 对象是否不等于右侧的 multiset 对象。  
  
```
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果集或多重集不相等，则为 **true**；如果相等，则为 **false**。  
  
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
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_lt_multiset"></a>operator&lt; (multiset)  
 测试运算符左侧的多重集对象是否小于右侧的多重集对象。  
  
```
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的多重集严格小于右侧的多重集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is not less than the multiset s3.  
*\  
```  
  
##  <a name="op_lt_eq_multiset"></a>operator&lt;= (multiset)  
 测试运算符左侧的多重集对象是否小于或等于右侧的多重集对象。  
  
```
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的多重集小于或等于右侧的多重集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
The multiset s1 is less than or equal to the multiset s2.  
The multiset s1 is greater than the multiset s3.  
The multiset s1 is less than or equal to the multiset s4.  
*\  
```  
  
##  <a name="op_eq_eq_multiset"></a>operator== (multiset)  
 测试运算符左侧的 multiset 对象是否等于右侧的 multiset 对象。  
  
```
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的多重集等于右侧的多重集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="op_gt_multiset"></a>operator&gt; (multiset)  
 测试运算符左侧的多重集对象是否大于右侧的多重集对象。  
  
```
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的多重集大于右侧的多重集，则为 **true**；否则为 **false**。  
  
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
\* Output:   
The multiset s1 is not greater than the multiset s2.  
The multiset s1 is greater than the multiset s3.  
*\  
```  
  
##  <a name="op_gt_eq_multiset"></a>operator&gt;= (multiset)  
 测试运算符左侧的多重集对象是否大于或等于右侧的多重集对象。  
  
```
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `multiset` 类型的对象。  
  
 `right`  
 一个 `multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的多重集大于或等于列表右侧的多重集，则为 **true**，否则为 **false**。  
  
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
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is greater than or equal to the multiset s3.  
The multiset s1 is greater than or equal to the multiset s4.  
*\  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<set>](../standard-library/set.md)




