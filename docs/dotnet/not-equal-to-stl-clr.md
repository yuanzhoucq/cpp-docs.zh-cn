---
title: not_equal_to (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::not_equal_to
dev_langs:
- C++
helpviewer_keywords:
- not_equal_to function [STL/CLR]
ms.assetid: 1b66e0ca-eace-4672-8da9-ed16f8608bca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b8046b4723a6e4e725662db2cce9e3981155748b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="notequalto-stlclr"></a>not_equal_to (STL/CLR)
此模板类描述某个函数，当调用时，返回 true，仅当第一个参数是否不等于第二个。 使用它指定根据其自变量类型的函数对象。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Arg>  
    ref class not_equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    not_equal_to();  
    not_equal_to(not_equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>参数  
 Arg  
 参数的类型。  
  
## <a name="member-functions"></a>成员函数  
  
|类型定义|描述|  
|---------------------|-----------------|  
|delegate_type|泛型委托的类型。|  
|first_argument_type|函子的第一个自变量的类型。|  
|result_type|函子结果的类型。|  
|second_argument_type|函子的第二个自变量的类型。|  
  
|成员|描述|  
|------------|-----------------|  
|not_equal_to|构造函数。|  
  
|运算符|描述|  
|--------------|-----------------|  
|operator()|计算所需的函数。|  
|运算符 delegate_type ^|强制转换为委托的函子。|  
  
## <a name="remarks"></a>备注  
 此模板类描述两个参数函子。 它定义了成员运算符`operator()`以便为函数调用时对象，它将返回 true 仅第一个参数是否不等于第二个。  
  
 你还可以作为其类型函数自变量传递对象`delegate_type^`和它将会相应地进行转换。  
  
## <a name="example"></a>示例  
  
```  
// cliext_not_equal_to.cpp   
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
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
0 1  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<功能 cliext/>  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)