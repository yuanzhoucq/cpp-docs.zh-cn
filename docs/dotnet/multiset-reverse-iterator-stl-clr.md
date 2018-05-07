---
title: 'multiset:: reverse_iterator (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- reverse_iterator member [STL/CLR]
ms.assetid: dde6ad36-ca59-4728-aa53-e3d117eb4f48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c8f9444769ba899b99ea66ccf3e7acdfaa1a1873
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="multisetreverseiterator-stlclr"></a>multiset::reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)   
 [multiset:: const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)   
 [multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)