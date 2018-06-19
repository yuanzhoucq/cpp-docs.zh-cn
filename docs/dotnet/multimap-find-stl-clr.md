---
title: 'multimap:: find (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::find
dev_langs:
- C++
helpviewer_keywords:
- find member [STL/CLR]
ms.assetid: 94b42497-3be4-448c-8de9-0a072ae14fbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ca6ee82246256c6bbc605e67dee5079f6eded04
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138237"
---
# <a name="multimapfind-stlclr"></a>multimap::find (STL/CLR)
查找与指定键匹配的元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 如果受控序列中的至少一个元素具有等效顺序与`key`，成员函数将返回指定这些元素之一的迭代器; 否则它将返回[multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md) `()`. 用于定位指定的键相匹配的受控序列中当前的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multimap_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymultimap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  
  
## <a name="description"></a>描述  
 请注意，`find`不保证其找到的多个元素。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多重映射 (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap:: equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)   
 [multimap:: lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)   
 [multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)