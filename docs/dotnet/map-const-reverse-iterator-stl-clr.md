---
title: "map:: const_reverse_iterator (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::const_reverse_iterator
dev_langs: C++
helpviewer_keywords: const_reverse_iterator member [STL/CLR]
ms.assetid: 056a765c-4f59-4bd8-99f4-c308a6f29c12
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ea55945736a73e9d7391e1d97383b1ad0487c6af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mapconstreverseiterator-stlclr"></a>map::const_reverse_iterator (STL/CLR)
受控序列的常量反向迭代器的类型...  
  
## <a name="syntax"></a>语法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T4`，可用作受控序列的常量反向迭代器。  
  
## <a name="example"></a>示例  
  
```  
// cliext_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [映射 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)