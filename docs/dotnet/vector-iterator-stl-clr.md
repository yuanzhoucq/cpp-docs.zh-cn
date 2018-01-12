---
title: "vector:: iterator (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::iterator
dev_langs: C++
helpviewer_keywords: iterator member [STL/CLR]
ms.assetid: a99932ac-c29e-4851-9331-9367f4dd9440
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e27743fd4d3cca3ad7783569dddac3af7e6d56c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vectoriterator-stlclr"></a>vector::iterator (STL/CLR)
受控序列的迭代器的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`，可用作受控序列的随机访问迭代器。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)