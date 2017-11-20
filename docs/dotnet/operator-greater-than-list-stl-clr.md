---
title: "运算符&gt;（列表） (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::operator>
dev_langs: C++
helpviewer_keywords: operator> member [STL/CLR]
ms.assetid: 58584708-1fa6-4908-84f6-790d53f46d9a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 272324af8bf4a0cd26e4763c8346669a4833ccd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="operatorgt-list-stlclr"></a>运算符&gt;（列表） (STL/CLR)
大于比较的列表。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
## <a name="remarks"></a>备注  
 运算符函数返回`right` `<` `left`。 用于测试是否`left`进行排序之后`right`当两个列表是元素的比较的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_operator_gt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [运算符 = = （列表） (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [运算符 ！ = （列表） (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [运算符\<（列表） (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)   
 [运算符 > = （列表） (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)