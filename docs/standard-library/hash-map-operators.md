---
title: "&lt;hash_map&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6960d7dfc3a6f36f803ae765ad4cbeb77038401c
ms.lasthandoff: 02/24/2017

---
# <a name="lthashmapgt-operators"></a>&lt;hash_map&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator!= (hash_map)](#operator_neq__hash_map_)|[operator==](#operator_eq_eq)|  
|[operator== (hash_map)](#operator_eq_eq__hash_map_)|  
  
##  <a name="operator_neq__hash_map_"></a>operator!= (hash_map)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 测试运算符左侧的 hash_map 对象是否不等于右侧的 hash_map 对象。  
  
```  
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `hash_map` 类型的对象。  
  
 `right`  
 一个 `hash_map` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 hash_map 不相等，则为 **true**；如果 hash_map 相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_map 对象之间的比较基于其元素的成对比较。 如果两个 hash_map 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_map 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_eq_eq__hash_map_"></a>operator== (hash_map)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 测试运算符左侧的 hash_map 对象是否等于右侧的 hash_map 对象。  
  
```  
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `hash_map` 类型的对象。  
  
 `right`  
 一个 `hash_map` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 hash_map 等于运算符右侧的 hash_map，则为 **true**，否则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_map 对象之间的比较基于其元素的成对比较。 如果两个 hash_map 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_map 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_neq"></a>operator!=  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 测试运算符左侧的 hash_multimap 对象是否不等于右侧的 hash_multimap 对象。  
  
```  
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `hash_multimap` 类型的对象。  
  
 `right`  
 一个 `hash_multimap` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果 hash_multimap 不相等，则为 **true**；如果 hash_multimap 相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_multimap 对象之间的比较基于其元素的成对比较。 如果两个 hash_multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multimap 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_eq_eq"></a>operator==  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 测试运算符左侧的 hash_multimap 对象是否等于右侧的 hash_multimap 对象。  
  
```  
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个 `hash_multimap` 类型的对象。  
  
 `right`  
 一个 `hash_multimap` 类型的对象。  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的 hash_multimap 等于运算符右侧的 hash_multimap，则为 **true**，否则为 **false**。  
  
### <a name="remarks"></a>备注  
 hash_multimap 对象之间的比较基于其元素的成对比较。 如果两个 hash_multimap 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multimap 相等。 否则，它们不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [<hash_map>](../standard-library/hash-map.md)


