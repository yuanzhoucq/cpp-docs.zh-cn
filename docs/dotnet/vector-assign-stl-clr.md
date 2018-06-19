---
title: 'vector:: assign (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 945e2048-6c61-4701-b13c-8241cbee3fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a16e9262ad69f6f4fe2e11030b5880485139823a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170409"
---
# <a name="vectorassign-stlclr"></a>vector::assign (STL/CLR)
替换所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 count  
 要插入的元素数。  
  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 右  
 要插入的枚举。  
  
 val  
 要插入的元素的值。  
  
## <a name="remarks"></a>备注  
 第一个成员函数将受控的序列替换的重复`count`值的元素`val`。 你使用它来填充容器元素与所有具有相同的值。  
  
 如果`InIt`是整数类型，第二个成员函数的行为与相同`assign((size_type)first, (value_type)last)`。 否则，它会替换受控的序列序列 [`first`， `last`)。 你使用它进行控制的序列副本另一个序列。  
  
 第三个成员函数与枚举器指定序列替换受控的序列`right`。 你可以使用它来使一个枚举器所描述的序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
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
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)