---
title: not1 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::not1
dev_langs:
- C++
helpviewer_keywords:
- not1 function [STL/CLR]
ms.assetid: a50cd819-10de-4d81-84da-8a34c5414a43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1ea947c86569a8725e372a31a9820f68984cfa27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137850"
---
# <a name="not1-stlclr"></a>not1 (STL/CLR)
生成`unary_negate`函子的。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Fun>  
    unary_negate<Fun> not1(Fun% functor);  
```  
  
## <a name="template-parameters"></a>模板参数  
 有趣  
 函子的类型。  
  
## <a name="function-parameters"></a>函数参数  
 函子  
 包装函数。  
  
## <a name="remarks"></a>备注  
 模板函数返回[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`。 您将其用作将单自变量函子包装在提供其逻辑非函子的简便方法。  
  
## <a name="example"></a>示例  
  
```  
// cliext_not1.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)