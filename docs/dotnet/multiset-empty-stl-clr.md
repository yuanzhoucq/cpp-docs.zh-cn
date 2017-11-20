---
title: "multiset:: empty (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiset::empty
dev_langs: C++
helpviewer_keywords: empty member [STL/CLR]
ms.assetid: 59ec9cc4-cc72-4082-9ab2-49b49980e681
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 289c885269c9c40690e58c33d481e4a4081eda00
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="multisetempty-stlclr"></a>multiset::empty (STL/CLR)
测试元素是否存在。  
  
## <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
## <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[multiset:: size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`。 用于测试是否多重集合为空。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_empty.cpp   
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
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)