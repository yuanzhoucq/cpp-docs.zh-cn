---
title: "hash_multimap:: const_iterator (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multimap::const_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_iterator member [STL/CLR]
ms.assetid: 3d54185c-7d30-41e6-8837-92e62448bc8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84cfd4f8926b1a11d909c02fb962bdd7d395c4f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimapconstiterator-stlclr"></a>hash_multimap::const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`，可用作受控序列的常量的双向迭代器。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multimap_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_multimap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)