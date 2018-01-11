---
title: "unary_negate (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::unary_negate
dev_langs: C++
helpviewer_keywords: unary_negate function [STL/CLR]
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 60e7a38ede07a3cf3b1c21b1c5fe26e9f588f2f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unarynegate-stlclr"></a>unary_negate (STL/CLR)
此模板类描述某个函数，当调用，返回的逻辑不其存储的单自变量函子。 使用它指定根据其存储的函子的函数对象。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>参数  
 有趣  
 存储函子的类型。  
  
## <a name="member-functions"></a>成员函数  
  
|类型定义|描述|  
|---------------------|-----------------|  
|argument_type|伪函数自变量的类型。|  
|delegate_type|泛型委托的类型。|  
|result_type|函子结果的类型。|  
  
|成员|描述|  
|------------|-----------------|  
|unary_negate|构造函数。|  
  
|运算符|描述|  
|--------------|-----------------|  
|operator()|计算所需的函数。|  
|delegate_type ^|强制转换为委托的函子。|  
  
## <a name="remarks"></a>备注  
 此模板类描述存储另一个单自变量函子的单自变量伪函数。 它定义了成员运算符`operator()`以便为函数调用时对象，它将返回逻辑的存储函子的不使用参数调用。  
  
 你还可以作为其类型函数自变量传递对象`delegate_type^`和它将会相应地进行转换。  
  
## <a name="example"></a>示例  
  
```  
// cliext_unary_negate.cpp   
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
  
## <a name="requirements"></a>惠?  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [not1 (STL/CLR)](../dotnet/not1-stl-clr.md)