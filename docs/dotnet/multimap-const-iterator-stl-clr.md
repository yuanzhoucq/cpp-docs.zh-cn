---
title: "multimap:: const_iterator (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap::const_iterator
dev_langs: C++
helpviewer_keywords: const_iterator member [STL/CLR]
ms.assetid: 13b166c9-1dcd-4ff9-b1da-3b8ffa463735
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e5faa25d8bce27558cd560cb5d6a2a27063d6653
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="multimapconstiterator-stlclr"></a>multimap::const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`，可用作受控序列的常量的双向迭代器。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multimap_const_iterator.cpp   
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
    Mymultimap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [多重映射 (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)