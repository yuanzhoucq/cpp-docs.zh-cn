---
title: "运算符&lt;(multiset) (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::operator<
dev_langs: C++
helpviewer_keywords: operator< member [STL/CLR]
ms.assetid: 48150cda-4f3e-4535-860c-89f622a7f0a8
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d2eef84b72ab36a0c4dbdfc02e4b58752126a7f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="operatorlt-multiset-stlclr"></a>运算符&lt;(multiset) (STL/CLR)
列表小于比较。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key>  
    bool operator<(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
## <a name="remarks"></a>备注  
 运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`很还 true， `left[i] < right[i]`。 否则，它将返回`left->size() < right->size()`用于测试是否`left`进行排序之前`right`当两个多重集是元素的比较的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [运算符 = = (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)   
 [运算符 ！ = (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)   
 [运算符 > = (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)   
 [运算符 > (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)   
 [operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)