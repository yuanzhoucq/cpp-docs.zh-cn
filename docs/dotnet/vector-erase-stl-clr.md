---
title: 'vector:: erase (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 624905eb-83c0-499b-a07a-c10aebd7acc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87e6d3dae3423763ec110e8999c6fd5ede1a6bc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170003"
---
# <a name="vectorerase-stlclr"></a>vector::erase (STL/CLR)
移除指定位置处的元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要清除范围的起点。  
  
 last  
 要清除范围的末尾。  
  
 其中  
 要清除的元素。  
  
## <a name="remarks"></a>备注  
 第一个成员函数将移除 `where` 所指向的受控序列的元素。 用于删除单个元素。  
  
 第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 用于删除零个或多个由连续的元素。  
  
 这两个成员函数返回一个迭代器，它指定已移除，任何元素之外保留的第一个元素或[vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()`如果此类元素不存在。  
  
 当清除元素，元素副本的数目呈线性擦除末尾和最近序列末尾之间的元素的数目。 （当清除序列的任意一端的一个或多个元素，没有元素副本会发生。）  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)