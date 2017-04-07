---
title: "&lt;vector&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 14308c0789851af423fd687f88acfe9177d89aff
ms.lasthandoff: 02/24/2017

---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_neq"></a>operator!=  
 测试运算符左侧的对象是否不等于右侧的对象。  
  
```  
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果 vector 不相等，则为 **true**；如果 vector 相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果两个 vector 具有的元素数目相等且对应元素具有相同的值，则两个 vector 相等。 否则，它们不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_ne.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
     v2.push_back( 2 );  
  
   if ( v1 != v2 )  
      cout << "Vectors not equal." << endl;  
   else  
      cout << "Vectors equal." << endl;  
}  
```  
  
```Output  
Vectors not equal.  
```  
  
##  <a name="operator_lt_"></a>operator&lt;  
 测试运算符左侧的对象是否小于右侧的对象。  
  
```  
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 vector 小于运算符右侧的 vector，则为 **true**；否则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_lt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 < v2 )  
      cout << "Vector v1 is less than vector v2." << endl;  
   else  
      cout << "Vector v1 is not less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than vector v2.  
```  
  
##  <a name="operator_lt__eq"></a>operator&lt;=  
 测试运算符左侧的对象是否小于或等于右侧的对象。  
  
```  
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 vector 小于或等于运算符右侧的 vector，则为 **true**；否则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_le.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 <= v2 )  
      cout << "Vector v1 is less than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than or equal to vector v2.  
```  
  
##  <a name="operator_eq_eq"></a>operator==  
 测试运算符左侧的对象是否等于右侧的对象。  
  
```  
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 vector 等于运算符右侧的 vector，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果两个 vector 具有的元素数目相等且对应元素具有相同的值，则两个 vector 相等。 否则，它们不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v2.push_back( 1 );  
  
   if ( v1 == v2 )  
      cout << "Vectors equal." << endl;  
   else  
      cout << "Vectors not equal." << endl;  
}  
```  
  
```Output  
Vectors equal.  
```  
  
##  <a name="operator_gt_"></a>operator&gt;  
 测试运算符左侧的对象是否大于右侧的对象。  
  
```  
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 vector 大于运算符右侧的 vector，则为 **true**；否则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_gt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
   v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 > v2 )  
      cout << "Vector v1 is greater than vector v2." << endl;  
   else  
      cout << "Vector v1 is not greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than vector v2.  
```  
  
##  <a name="operator_gt__eq"></a>operator&gt;=  
 测试运算符左侧的对象是否大于或等于右侧的对象。  
  
```  
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 类型 **vector** 的对象。  
  
 `right`  
 类型 **vector** 的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 vector 大于或等于运算符右侧的 vector，则为 **true**；否则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_op_ge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
     v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 >= v2 )  
      cout << "Vector v1 is greater than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than or equal to vector v2.  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<vector>](../standard-library/vector.md)


