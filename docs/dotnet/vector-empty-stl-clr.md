---
title: 'vector:: empty (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::empty
dev_langs:
- C++
helpviewer_keywords:
- empty member [STL/CLR]
ms.assetid: c09fc4a3-bd79-4458-9a36-1d9c82ac36b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 23cb3455db73d1f16599222548625df9c9578544
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167520"
---
# <a name="vectorempty-stlclr"></a>vector::empty (STL/CLR)
测试元素是否存在。  
  
## <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
## <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`。 你可以使用它来测试是否向量为空。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_empty.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
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
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)