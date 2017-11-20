---
title: "运算符&lt;= （向量） (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::operator<=
dev_langs: C++
helpviewer_keywords: operator<= member [STL/CLR]
ms.assetid: d4f9d0ba-1fa3-4895-aef4-c9f9a06dbe05
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e2b2e9cc116c06cb1f0c91d093566fa8ac77eac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-vector-stlclr"></a>运算符&lt;= （向量） (STL/CLR)
矢量小于或等于比较。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
## <a name="remarks"></a>备注  
 运算符函数返回`!(right < left)`。 用于测试是否`left`未进行排序之后`right`两个向量何时比较的元素的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_operator_le.cpp   
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
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [运算符 = = （向量） (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)   
 [运算符 ！ = （向量） (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)   
 [运算符\<（向量） (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [运算符 > = （向量） (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)   
 [operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)