---
title: "vector:: vector (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::vector
dev_langs: C++
helpviewer_keywords: vector member [STL/CLR]
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a321e18c9fc921e1d88961b4f282c29917fa7962
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vectorvector-stlclr"></a>vector::vector (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 count  
 要插入的元素数。  
  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 右  
 要插入的对象或范围。  
  
 val  
 要插入的元素的值。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `vector();`  
  
 初始化受控的序列不包含任何元素。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `vector(vector<Value>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)。 用于指定的初始受控的序列的向量对象所控制的序列副本`right`。  
  
 构造函数：  
  
 `vector(vector<Value>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)。 用于指定是由其句柄的向量对象控制的序列的副本的初始受控的序列`right`。  
  
 构造函数：  
  
 `explicit vector(size_type count);`  
  
 初始化受控的序列与`count`元素每个值`value_type()`。 你使用它来填充容器元素与所有具有默认值。  
  
 构造函数：  
  
 `vector(size_type count, value_type val);`  
  
 初始化受控的序列与`count`元素每个值`val`。 你使用它来填充容器元素与所有具有相同的值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 初始化受控的序列与序列 [`first`， `last`)。 你可以使用它以使另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`。 你可以使用它来使一个枚举器所描述的另一个序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)