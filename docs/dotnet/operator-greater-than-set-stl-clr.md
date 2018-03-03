---
title: "运算符&gt;(set) (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set::operator>
dev_langs:
- C++
helpviewer_keywords:
- operator> member [STL/CLR]
ms.assetid: 1af7a3bd-011e-4248-902a-f86d4acae856
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6f6f92d2e5200ea86b6db5622ef6d9e9a39430fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="operatorgt-set-stlclr"></a>运算符&gt;(set) (STL/CLR)
大于比较的列表。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key>  
    bool operator>(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
## <a name="remarks"></a>备注  
 运算符函数返回`right` `<` `left`。 用于测试是否`left`进行排序之后`right`当两个集是元素的比较的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_set_operator_gt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
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
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [运算符 = = (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)   
 [运算符 ！ = (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)   
 [运算符\<(set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)   
 [运算符 > = (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)   
 [operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)