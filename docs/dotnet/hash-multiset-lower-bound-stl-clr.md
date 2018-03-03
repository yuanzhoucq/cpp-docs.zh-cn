---
title: "hash_multiset:: lower_bound (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: 891898fa-c9e8-4132-a71d-36e5141793f1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fb799c12bf153ed3279d8d3d6fb10d59bd1cf22d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetlowerbound-stlclr"></a>hash_multiset::lower_bound (STL/CLR)
查找与指定的键匹配的范围开始处。  
  
## <a name="syntax"></a>语法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 成员函数将确定第一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，它将返回[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; 否则它将返回指定的迭代器`X`。 用于当前与指定的键匹配的控制序列中查找的元素序列的开头。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset:: count (STL/CLR)](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash_multiset:: equal_range (STL/CLR)](../dotnet/hash-multiset-equal-range-stl-clr.md)   
 [hash_multiset:: find (STL/CLR)](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)