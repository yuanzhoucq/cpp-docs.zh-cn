---
title: 'deque:: deque (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::deque
dev_langs:
- C++
helpviewer_keywords:
- deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 433b6ff053db0c642c2a81a5765755c9f42e1a0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 `count`  
 要插入的元素数。  
  
 `first`  
 要插入的范围开始处。  
  
 `last`  
 要插入的范围的末尾。  
  
 `right`  
 要插入的对象或范围。  
  
 `val`  
 要插入的元素的值。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `deque();`  
  
 初始化受控的序列不包含任何元素。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `deque(deque<Value>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)。 用于指定的初始受控的序列的 deque 对象所控制的序列副本`right`。 有关迭代器的详细信息，请参阅[deque:: begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)和[deque:: end (STL/CLR)](../dotnet/deque-end-stl-clr.md)。  
  
 构造函数：  
  
 `deque(deque<Value>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)。 用于指定是由其句柄的 deque 对象控制的序列的副本的初始受控的序列`right`。  
  
 构造函数：  
  
 `explicit deque(size_type count);`  
  
 初始化受控的序列与`count`元素每个值`value_type()`。 你使用它来填充容器元素与所有具有默认值。  
  
 构造函数：  
  
 `deque(size_type count, value_type val);`  
  
 初始化受控的序列与`count`元素每个值`val`。 你使用它来填充容器元素与所有具有相同的值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 初始化受控的序列与序列 [`first`， `last`)。 你可以使用它以使另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`。 你可以使用它来使一个枚举器所描述的另一个序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)