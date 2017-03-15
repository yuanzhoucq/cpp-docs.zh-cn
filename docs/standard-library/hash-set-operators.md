---
title: "&lt;hash_set&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 031904042e81f5ec9c8b54bbc3e2bfa9e9a365cf
ms.lasthandoff: 02/24/2017

---
# <a name="lthashsetgt-operators"></a>&lt;hash_set&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator!= (hash_multiset)](#operator_neq__hash_multiset_)|[operator==](#operator_eq_eq)|  
|[operator== (hash_multiset)](#operator_eq_eq__hash_multiset_)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>operator!=  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 测试运算符左侧的 hash_set 对象是否不等于右侧的 hash_set 对象。  
  
```  
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 一个 `hash_set` 类型的对象。  
  
 ` right`  
 一个 `hash_set` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 hash_set 不相等，则为 **true**；如果 hash_set 相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_set 对象之间的比较基于其元素的成对比较。 如果两个 hash_set 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_set 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_sets hs1 and hs2 are not equal.  
The hash_sets hs1 and hs3 are equal.  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>operator==  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 测试运算符左侧的 hash_set 对象是否等于右侧的 hash_set 对象。  
  
```  
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 一个 `hash_set` 类型的对象。  
  
 ` right`  
 一个 `hash_set` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 hash_set 等于运算符右侧的 hash_set，则为 **true**，否则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_set 对象之间的比较基于其元素的成对比较。 如果两个 hash_set 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_set 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_set_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_sets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_sets s1 and s3 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s3 are not equal." << endl;  
}  
```  
  
```Output  
The hash_sets s1 and s2 are not equal.  
The hash_sets s1 and s3 are equal.  
```  
  
##  <a name="a-nameoperatorneqhashmultiseta--operator-hashmultiset"></a><a name="operator_neq__hash_multiset_"></a>operator!= (hash_multiset)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 测试运算符左侧的 hash_multiset 对象是否不等于右侧的 hash_multiset 对象。  
  
```  
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 一个 `hash_multiset` 类型的对象。  
  
 ` right`  
 一个 `hash_multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 hash_multiset 不相等，则为 **true**；如果 hash_multiset 相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_multiset 对象之间的比较基于其元素的成对比较。 如果两个 hash_multiset 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multiset 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hashset_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_multisets hs1 and hs2 are not equal.  
The hash_multisets hs1 and hs3 are equal.  
```  
  
##  <a name="a-nameoperatoreqeqhashmultiseta--operator-hashmultiset"></a><a name="operator_eq_eq__hash_multiset_"></a>operator== (hash_multiset)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 测试运算符左侧的 hash_multiset 对象是否等于右侧的 hash_multiset 对象。  
  
```  
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 一个 `hash_multiset` 类型的对象。  
  
 ` right`  
 一个 `hash_multiset` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 hash_multiset 等于运算符右侧的 hash_multiset，则为 **true**，否则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_multiset 对象之间的比较基于其元素的成对比较。 如果两个 hash_multiset 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multiset 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// hash_multiset_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
}  
```  
  
```Output  
The hash_multisets s1 and s2 are not equal.  
The hash_multisets s1 and s2 are equal.  
```  
  
## <a name="see-also"></a>另请参阅  
 [<hash_set>](../standard-library/hash-set.md)


