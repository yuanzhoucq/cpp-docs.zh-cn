---
title: 'multimap:: multimap (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::multimap
dev_langs:
- C++
helpviewer_keywords:
- multimap member [STL/CLR]
ms.assetid: cdf9c5dc-774c-424e-aeea-7554643e401c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84d0243ca39aae230f3cfe42d53fdf33d48b7314
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="multimapmultimap-stlclr"></a>multimap::multimap (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
multimap();  
explicit multimap(key_compare^ pred);  
multimap(multimap<Key, Mapped>% right);  
multimap(multimap<Key, Mapped>^ right);  
template<typename InIter>  
    multimapmultimap(InIter first, InIter last);  
template<typename InIter>  
    multimap(InIter first, InIter last,  
        key_compare^ pred);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 pred  
 排序受控序列的谓词。  
  
 右  
 要插入的对象或范围。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `multimap();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`。 用于指定空的初始受控的序列，使用默认的排序谓词。  
  
 构造函数：  
  
 `explicit multimap(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`。 用于指定空的初始受控的序列，通过指定排序的谓词。  
  
 构造函数：  
  
 `multimap(multimap<Key, Mapped>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)，使用默认的排序谓词。 用于指定是通过多重映射对象控制的序列的副本的初始受控的序列`right`，使用默认的排序谓词。  
  
 构造函数：  
  
 `multimap(multimap<Key, Mapped>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)，使用默认的排序谓词。 用于指定是通过多重映射对象控制的序列的副本的初始受控的序列`right`，使用默认的排序谓词。  
  
 构造函数：  
  
 `template<typename InIter> multimap(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)，使用默认的排序谓词。 你可以使用它以使用默认的排序谓词使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> multimap(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`。 你可以使用它以使另一个序列，使用指定的排序谓词的副本的受控的序列。  
  
 构造函数：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`，使用默认的排序谓词。 你可以使用它来使一个枚举器，使用默认的排序谓词所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`。 你可以使用它来使受控的序列的枚举，通过指定排序的谓词所描述的另一个序列的副本。  
  
## <a name="example"></a>示例  
  
```cpp  
// cliext_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
// construct an empty container   
    Mymultimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultimap c3(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3);   
    for each (Mymultimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultimap c7(c4);   
    for each (Mymultimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymultimap c8(%c3);   
    for each (Mymultimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多重映射 (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)