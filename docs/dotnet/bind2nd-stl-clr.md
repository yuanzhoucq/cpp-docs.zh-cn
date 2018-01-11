---
title: "bind2nd (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::bind2nd
dev_langs: C++
helpviewer_keywords: bind2nd function [STL/CLR]
ms.assetid: 457cebea-38e4-4466-a468-fe9eb138e80c
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3617cb917012a48398c6c9f530c2419aa8ea195b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bind2nd-stlclr"></a>bind2nd (STL/CLR)
生成`binder2nd`有关自变量，以及函子。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Fun,  
    typename Arg>  
    binder2nd<Fun> bind2nd(Fun% functor,  
        Arg right);  
```  
  
## <a name="template-parameters"></a>模板参数  
 Arg  
 自变量类型。  
  
 有趣  
 函子的类型。  
  
## <a name="function-parameters"></a>函数参数  
 函子  
 包装函数。  
  
 右  
 要包装的第二个参数。  
  
## <a name="remarks"></a>备注  
 模板函数返回[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`。 你将它用作一种简便方式将两个参数函子和其第二个自变量包装在使用第一个参数调用它的单自变量伪函数。  
  
## <a name="example"></a>示例  
  
```  
// cliext_bind2nd.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)