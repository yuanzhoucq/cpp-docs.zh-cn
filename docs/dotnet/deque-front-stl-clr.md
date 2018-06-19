---
title: 'deque:: front (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::front
dev_langs:
- C++
helpviewer_keywords:
- front member [STL/CLR]
ms.assetid: eb8cb5f2-346d-4d7a-bb7b-cf67fe4318e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aac8eda38b442f0169e7cc27a6228c7668c43634
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111727"
---
# <a name="dequefront-stlclr"></a>deque::front (STL/CLR)
访问第一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
reference front();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的第一个元素的引用。 你可以使用它来读取或写入的第一个元素，当你知道它存在。  
  
## <a name="example"></a>示例  
  
```  
// cliext_deque_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: back (STL/CLR)](../dotnet/deque-back-stl-clr.md)   
 [deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)   
 [deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)