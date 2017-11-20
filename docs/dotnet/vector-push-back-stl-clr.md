---
title: "vector:: push_back (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::push_back
dev_langs: C++
helpviewer_keywords: push_back member [STL/CLR]
ms.assetid: 4a4c302b-e29f-4b68-b759-2f831814d896
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15543574c29cea7bab8e99cc2e96d891c03c1282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="vectorpushback-stlclr"></a>vector::push_back (STL/CLR)
添加新的最后一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
void push_back(value_type val);  
```  
  
## <a name="remarks"></a>备注  
 成员函数将插入具有值的元素`val`受控序列的末尾。 你可以使用它要追加到向量的另一个元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)