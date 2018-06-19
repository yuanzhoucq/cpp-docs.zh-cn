---
title: 'multiset:: multiset (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::multiset
dev_langs:
- C++
helpviewer_keywords:
- multiset member [STL/CLR]
ms.assetid: a6ddb2df-d7cd-4b12-aee7-81da1f67f57f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f890a7051d6764f2168c5d90859219fb3513031e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136101"
---
# <a name="multisetmultiset-stlclr"></a>multiset::multiset (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
multiset();  
explicit multiset(key_compare^ pred);  
multiset(multiset<Key>% right);  
multiset(multiset<Key>^ right);  
template<typename InIter>  
    multisetmultiset(InIter first, InIter last);  
template<typename InIter>  
    multiset(InIter first, InIter last,  
        key_compare^ pred);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `multiset();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`。 用于指定空的初始受控的序列，使用默认的排序谓词。  
  
 构造函数：  
  
 `explicit multiset(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`。 用于指定空的初始受控的序列，通过指定排序的谓词。  
  
 构造函数：  
  
 `multiset(multiset<Key>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)，使用默认的排序谓词。 用于指定是通过多重集对象控制的序列的副本的初始受控的序列`right`，使用默认的排序谓词。  
  
 构造函数：  
  
 `multiset(multiset<Key>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)，使用默认的排序谓词。 用于指定是通过多重集对象控制的序列的副本的初始受控的序列`right`，使用默认的排序谓词。  
  
 构造函数：  
  
 `template<typename InIter> multiset(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)，使用默认的排序谓词。 你可以使用它以使用默认的排序谓词使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`。 你可以使用它以使另一个序列，使用指定的排序谓词的副本的受控的序列。  
  
 构造函数：  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`，使用默认的排序谓词。 你可以使用它来使一个枚举器，使用默认的排序谓词所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`。 你可以使用它来使受控的序列的枚举，通过指定排序的谓词所描述的另一个序列的副本。  
  
## <a name="example"></a>示例  
  
```cpp  
// cliext_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
// construct an empty container   
    Mymultiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mymultiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)   
 [multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)