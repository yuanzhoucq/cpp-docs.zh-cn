---
title: 'multimap:: lower_bound (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: b8f9b2c2-ebcd-4553-b410-75fd8d472a49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2267f889a27a1b48989c5bd9aebe9dd9b7722e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135380"
---
# <a name="multimaplowerbound-stlclr"></a>multimap::lower_bound (STL/CLR)
查找与指定的键匹配的范围开始处。  
  
## <a name="syntax"></a>语法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 成员函数将确定第一个元素`X`受控序列中具有等效顺序到`key`。 如果此类元素不存在，它将返回[multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; 否则它将返回指定的迭代器`X`。 用于当前与指定的键匹配的控制序列中查找的元素序列的开头。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multimap_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymultimap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多重映射 (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap:: count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)   
 [multimap:: equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)   
 [multimap:: find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)   
 [multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)