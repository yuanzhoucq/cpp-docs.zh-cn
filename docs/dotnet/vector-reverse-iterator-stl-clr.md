---
title: 'vector:: reverse_iterator (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- reverse_iterator member [STL/CLR]
ms.assetid: 0a90c5ee-a95f-4f71-a027-f1668000ccd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e56c25735cd8f0fd7fdf374ce8edfa512d8b6f1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168381"
---
# <a name="vectorreverseiterator-stlclr"></a>vector::reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)   
 [vector:: const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)   
 [vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)