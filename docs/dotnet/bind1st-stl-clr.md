---
title: bind1st (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::bind1st
dev_langs:
- C++
helpviewer_keywords:
- bind1st function [STL/CLR]
ms.assetid: 03a04cef-60fb-4667-b22a-22a387adb028
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d602a7422fc9ccc971508b915f6228ffd1659664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105369"
---
# <a name="bind1st-stlclr"></a>bind1st (STL/CLR)
生成`binder1st`有关自变量，以及函子。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
## <a name="template-parameters"></a>模板参数  
 Arg  
 自变量类型。  
  
 有趣  
 函子的类型。  
  
## <a name="function-parameters"></a>函数参数  
 函子  
 包装函数。  
  
 左  
 要包装的第一个参数。  
  
## <a name="remarks"></a>备注  
 模板函数返回[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`。 你将它用作一种简便方式中调用它与第二个参数的单自变量涵子包装两个参数函子和其第一个参数。  
  
## <a name="example"></a>示例  
  
```  
// cliext_bind1st.cpp   
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
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)