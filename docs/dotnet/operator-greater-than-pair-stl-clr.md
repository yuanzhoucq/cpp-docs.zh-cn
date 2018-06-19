---
title: 运算符&gt;（对） (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::operator>
dev_langs:
- C++
helpviewer_keywords:
- operator> member [STL/CLR]
ms.assetid: c392a696-3425-49c8-9ddf-be2f2d2dd42e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 30b388bbe60d252c15ca77c749f48e5b2b8a8e87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134099"
---
# <a name="operatorgt-pair-stlclr"></a>运算符&gt;（对） (STL/CLR)
对大于比较。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左的对。  
  
 右  
 要比较的右对。  
  
## <a name="remarks"></a>备注  
 运算符函数返回`right` `<` `left`。 用于测试是否`left`进行排序之后`right`时的两个对是元素的比较的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_pair_operator_gt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] > [x 3] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[x 4] > [x 3] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] > [x 3] is False  
[x 4] > [x 3] is True  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/实用工具 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [对 (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [运算符 = = （对） (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [运算符 ！ = （对） (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [运算符\<（对） (STL/CLR)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [运算符 > = （对） (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)