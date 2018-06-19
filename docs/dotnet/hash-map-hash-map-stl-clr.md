---
title: 'hash_map:: hash_map (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::hash_map
dev_langs:
- C++
helpviewer_keywords:
- hash_map member [STL/CLR]
ms.assetid: d65eb3fa-4bf9-4186-95f8-5517c90ef1fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be0eedeea8aceabbb6726f27a5cd488beeee50f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33118915"
---
# <a name="hashmaphashmap-stlclr"></a>hash_map::hash_map (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
hash_map();  
explicit hash_map(key_compare^ pred);  
hash_map(key_compare^ pred, hasher^ hashfn);  
hash_map(hash_map<Key, Mapped>% right);  
hash_map(hash_map<Key, Mapped>^ right);  
template<typename InIter>  
    hash_maphash_map(InIter first, InIter last);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要插入的范围开始处。  
  
 hashfn  
 哈希与存储桶的映射键的函数。  
  
 last  
 要插入的范围的末尾。  
  
 pred  
 排序受控序列的谓词。  
  
 右  
 要插入的对象或范围。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `hash_map();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `explicit hash_map(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用指定的排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_map(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用哈希运算`hashfn`。 用于指定空的初始受控的序列，使用指定的排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_map 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_map 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)、 排序谓词，默认值和默认哈希函数。 你可以使用它以使用默认的排序谓词和哈希函数使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使另一个序列，使用指定的排序谓词和默认哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使另一个序列，使用指定的排序谓词和哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`、 排序谓词，默认值和默认哈希函数。 你可以使用它来使一个枚举器，使用默认的排序谓词和哈希函数所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使所描述的枚举，使用指定排序谓词和默认哈希的函数的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使所描述的枚举，使用指定的排序谓词和哈希函数的另一个序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_map_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
// construct an empty container   
    Myhash_map c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_map c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_map c3(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_map c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_map c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_map c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3);   
    for each (Myhash_map::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_map c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_map c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_map c7(c4);   
    for each (Myhash_map::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_map c8(%c3);   
    for each (Myhash_map::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::generic_container (STL/CLR)](../dotnet/hash-map-generic-container-stl-clr.md)   
 [hash_map::operator= (STL/CLR)](../dotnet/hash-map-operator-assign-stl-clr.md)