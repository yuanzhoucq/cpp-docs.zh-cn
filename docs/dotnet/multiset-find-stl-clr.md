---
title: "multiset:: find (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::find
dev_langs:
- C++
helpviewer_keywords:
- find member [STL/CLR]
ms.assetid: 162c9002-fb34-44f9-8e42-6bacecd0ebbc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84a04f31c0833222d4bbef598a463d35efc816fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multisetfind-stlclr"></a>multiset::find (STL/CLR)
查找与指定键匹配的元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 如果受控序列中的至少一个元素具有等效顺序与`key`，成员函数将返回指定这些元素之一的迭代器; 否则它将返回[multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()`. 用于定位指定的键相匹配的受控序列中当前的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
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
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  
  
## <a name="description"></a>描述  
 请注意，`find`不保证其找到的多个元素。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)   
 [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)   
 [multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)