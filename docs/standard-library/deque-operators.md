---
title: "&lt;deque&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 18fafc735fe05dbba24058394bbcd7fefd45cffd
ms.lasthandoff: 02/24/2017

---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 测试运算符左侧的 deque 对象是否不等于右侧的 deque 对象。  
  
```
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
The deques are not equal.  
*\  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 测试运算符左侧的 deque 对象是否小于右侧的 deque 对象。  
  
```
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
Deque c1 is less than deque c2.  
*\   
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 测试运算符左侧的 deque 对象是否小于或等于右侧的 deque 对象。  
  
```
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
Deque c1 is less than or equal to deque c2.  
*\  
  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 测试运算符左侧的 deque 对象是否等于右侧的 deque 对象。  
  
```
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
The deques are equal.  
The deques are not equal.  
*\  
  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 测试运算符左侧的 deque 对象是否大于右侧的 deque 对象。  
  
```
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
Deque c1 is greater than deque c2.  
*\  
  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 测试运算符左侧的 deque 对象是否大于或等于右侧的 deque 对象。  
  
```
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `deque` 类型的对象。  
  
 `right`  
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
\* Output:   
Deque c1 is greater than or equal to deque c2.  
*\  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<deque>](../standard-library/deque.md)




