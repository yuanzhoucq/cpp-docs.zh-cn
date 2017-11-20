---
title: "multiset:: end (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::end
dev_langs: C++
helpviewer_keywords: end member [STL/CLR]
ms.assetid: 225f8b74-f9b9-47ea-9603-43ac7c9a9734
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 92a7604c30070cc7b2023a73ecc4285a8d5152d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="multisetend-stlclr"></a>multiset::end (STL/CLR)
指定受控序列的末尾。  
  
## <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回的双向迭代器，它指向刚超出受控序列的末尾。 用于获取指定的受控序列中; 末尾的迭代器其状态不更改如果更改了受控序列的长度。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_end.cpp   
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
  
// inspect last two items   
    Mymultiset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)