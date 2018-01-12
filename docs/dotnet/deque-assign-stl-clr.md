---
title: "deque:: assign (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::assign
dev_langs: C++
helpviewer_keywords: assign member [STL/CLR]
ms.assetid: 03fafdbb-6b10-4464-b3dc-0cc5cb8ac980
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1ae8bb7a21a336987d30cb41a7a1ff9d586db830
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dequeassign-stlclr"></a>deque::assign (STL/CLR)
替换所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 `count`  
 要插入的元素数。  
  
 `first`  
 要插入的范围开始处。  
  
 `last`  
 要插入的范围的末尾。  
  
 `right`  
 要插入的枚举。  
  
 `val`  
 要插入的元素的值。  
  
## <a name="remarks"></a>备注  
 第一个成员函数将受控的序列替换的重复`count`值的元素`val`。 你使用它来填充容器元素与所有具有相同的值。  
  
 如果`InIt`是整数类型，第二个成员函数的行为与相同`assign((size_type)first, (value_type)last)`。 否则，它会替换受控的序列序列 [`first`， `last`)。 你使用它进行控制的序列副本另一个序列。  
  
 第三个成员函数与枚举器指定序列替换受控的序列`right`。 你可以使用它来使一个枚举器所描述的序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```cpp  
// cliext_deque_assign.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)