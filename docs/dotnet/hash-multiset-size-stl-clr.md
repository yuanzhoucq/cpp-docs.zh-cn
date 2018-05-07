---
title: 'hash_multiset:: size (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::size
dev_langs:
- C++
helpviewer_keywords:
- size member [STL/CLR]
ms.assetid: 45f1f35e-35c4-4e39-8485-0786c1de22e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3027eb62115fb240b77a84a7a006b8b567725dc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultisetsize-stlclr"></a>hash_multiset::size (STL/CLR)
对元素数进行计数。  
  
## <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[hash_multiset:: empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multiset_size.cpp   
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
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)