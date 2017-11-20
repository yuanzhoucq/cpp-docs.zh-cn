---
title: "&lt;utility&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
dev_langs: C++
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
caps.latest.revision: "13"
manager: ghogen
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 9f9290b171a74098af5186c17f027fcf6e34c78f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ltutilitygt-operators"></a>&lt;utility&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator!=  
 测试运算符左侧和右侧的 pair 对象是否不相等。  
  
```  
template <class Type>  
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **pair** 的对象。  
  
 `right`  
 一个 `pair` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果对不相等，则为 **true**；如果对相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果两个对的每个元素对应相等，则这两个对相等。 如果一个对的第一个或第二个元素不等于另一个对的相应元素，则这两个对不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_ne.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 != p2 )  
      cout << "The pairs p1 and p2 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are equal." << endl;  
  
   if ( p1 != p3 )  
      cout << "The pairs p1 and p3 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are equal." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.111 ).  
The pair p2 is: ( 1000, 0.00111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pairs p1 and p2 are not equal.  
The pairs p1 and p3 are equal.  
```  
  
##  <a name="op_eq_eq"></a>operator==  
 测试运算符左侧和右侧的 pair 对象是否相等。  
  
```  
template <class T, class U>  
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **pair** 的对象。  
  
 `right`  
 一个 `pair` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果两个 pair 相等，则为 **true**；如果 `pair` 不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果两个对的每个元素对应相等，则这两个对相等。 该函数返回 `left`。 **first** == `right`。 **first** && `left`。 **second** == `right`。 **second**。 如果一个对的第一个或第二个元素不等于另一个对的相应元素，则这两个对不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_eq.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 == p2 )  
      cout << "The pairs p1 and p2 are equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are not equal." << endl;  
  
   if ( p1 == p3 )  
      cout << "The pairs p1 and p3 are equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are not equal." << endl;  
}  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 测试运算符左侧的 pair 对象是否小于右侧的 pair 对象。  
  
```  
template <class T, class U>  
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 运算符左侧类型 `pair` 的对象。  
  
 `right`  
 运算符右侧类型 `pair` 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 `pair` 完全小于运算符右侧的 `pair`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 `left` `pair`认为对象严格小于`right``pair`对象如果`left`小于且不等于`right`。  
  
 在配对比较中，两个对的值的第一个元素具有最高优先级。 如果它们不同，则将其比较结果作为配对比较的结果。 如果第一个元素的值不同，则比较第二个元素的值，并将其比较结果作为配对比较的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_lt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 < p2 )  
      cout << "The pair p1 is less than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p2." << endl;  
  
   if ( p1 < p3 )  
      cout << "The pair p1 is less than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p3." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pair p1 is less than the pair p2.  
The pair p1 is not less than the pair p3.  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 测试运算符左侧的 pair 对象是否小于或等于右侧的 pair 对象。  
  
```  
template <class Type>  
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 运算符左侧类型 `pair` 的对象。  
  
 `right`  
 运算符右侧类型 `pair` 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 `pair` 小于或等于右侧的 `pair`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 在配对比较中，两个对的值的第一个元素具有最高优先级。 如果它们不同，则将其比较结果作为配对比较的结果。 如果第一个元素的值不同，则比较第二个元素的值，并将其比较结果作为配对比较的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_le.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 <= p2 )  
      cout << "The pair p1 is less than or equal to the pair p2." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p2." << endl;  
  
   if ( p1 <= p3 )  
      cout << "The pair p1 is less than or equal to the pair p3." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p3." << endl;  
  
   if ( p1 <= p4 )  
      cout << "The pair p1 is less than or equal to the pair p4." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than or equal to the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is less than or equal to the pair p4.  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 测试运算符左侧的 pair 对象是否大于右侧的 pair 对象。  
  
```  
template <class Type>  
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 运算符左侧类型 `pair` 的对象。  
  
 `right`  
 运算符右侧类型 `pair` 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 `pair` 完全大于右侧的 `pair`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 `left` `pair`认为对象要严格大于`right``pair`对象如果`left`大于且不等于`right`。  
  
 在配对比较中，两个对的值的第一个元素具有最高优先级。 如果它们不同，则将其比较结果作为配对比较的结果。 如果第一个元素的值不同，则比较第二个元素的值，并将其比较结果作为配对比较的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_gt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 > p2 )  
      cout << "The pair p1 is greater than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p2." << endl;  
  
   if ( p1 > p3 )  
      cout << "The pair p1 is greater than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p3." << endl;  
  
   if ( p1 > p4 )  
      cout << "The pair p1 is greater than the pair p4." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is not greater than the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is not greater than the pair p4.  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 测试运算符左侧的 pair 对象是否大于或等于右侧的 pair 对象。  
  
```  
template <class Type>  
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 运算符左侧类型 `pair` 的对象。  
  
 `right`  
 运算符右侧类型 `pair` 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 `pair` 大于或等于右侧的 `pair`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 在配对比较中，两个对的值的第一个元素具有最高优先级。 如果它们不同，则将其比较结果作为配对比较的结果。 如果第一个元素的值不同，则比较第二个元素的值，并将其比较结果作为配对比较的结果。  
  
### <a name="example"></a>示例  
  
```cpp  
// utility_op_ge.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 >= p2 )  
      cout << "Pair p1 is greater than or equal to pair p2." << endl;  
   else  
      cout << "The pair p1 is less than the pair p2." << endl;  
  
   if ( p1 >= p3 )  
      cout << "Pair p1 is greater than or equal to pair p3." << endl;  
   else  
      cout << "The pair p1 is less than the pair p3." << endl;  
  
   if ( p1 >= p4 )  
      cout << "Pair p1 is greater than or equal to pair p4." << endl;  
   else  
      cout << "The pair p1 is less than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than the pair p2.  
Pair p1 is greater than or equal to pair p3.  
Pair p1 is greater than or equal to pair p4.  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<utility>](../standard-library/utility.md)

