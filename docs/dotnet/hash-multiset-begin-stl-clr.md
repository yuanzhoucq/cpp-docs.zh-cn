---
title: "hash_multiset:: begin (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::begin
dev_langs: C++
helpviewer_keywords: begin member [STL/CLR]
ms.assetid: f03fc205-cbc9-4054-ac6d-41ad526edfea
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8dedb4890ab4d389386a7a01f9805403c726ac83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultisetbegin-stlclr"></a>hash_multiset::begin (STL/CLR)
指定受控序列的开头。  
  
## <a name="syntax"></a>语法  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回指定的受控序列，或刚超出空序列末尾的第一个元素的双向迭代器。 用于获取指定的迭代器`current`如果受控序列的长度发生更改，可以更改的受控的序列中，但其状态的开头。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multiset_begin.cpp   
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
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)