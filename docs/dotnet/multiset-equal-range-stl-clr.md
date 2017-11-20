---
title: "multiset:: equal_range (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::equal_range
dev_langs: C++
helpviewer_keywords: equal_range member [STL/CLR]
ms.assetid: 0fa617fb-8316-4310-b906-0322fa04aebe
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e03ecf53edf4f5eb0e792aca3d4cb1008bbdc6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="multisetequalrange-stlclr"></a>multiset::equal_range (STL/CLR)
查找与指定键匹配的范围。  
  
## <a name="syntax"></a>语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 成员函数将返回一对迭代器`cliext::pair<iterator, iterator>(` [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [multiset:: upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`。 你可以使用它来确定的受控序列中的当前与指定的键匹配的元素范围。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
typedef Mymultiset::pair_iter_iter Pairii;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)   
 [multiset:: find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)   
 [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)   
 [multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)