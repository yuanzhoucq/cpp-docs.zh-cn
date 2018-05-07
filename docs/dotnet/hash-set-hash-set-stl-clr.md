---
title: 'hash_set:: hash_set (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_set
dev_langs:
- C++
helpviewer_keywords:
- hash_set member [STL/CLR]
ms.assetid: 006414ed-db5a-4c08-ac81-4a8ae57d0aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e0f8ce11d66b02c63d2eee6cf2022c16c214fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hashsethashset-stlclr"></a>hash_set::hash_set (STL/CLR)
构造容器对象。  
  
## <a name="syntax"></a>语法  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_set();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `explicit hash_set(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用指定的排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用哈希运算`hashfn`。 用于指定空的初始受控的序列，使用指定的排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_set(hash_set<Key>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_set 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_set(hash_set<Key>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_set 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)、 排序谓词，默认值和默认哈希函数。 你可以使用它以使用默认的排序谓词和哈希函数使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使另一个序列，使用指定的排序谓词和默认哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使另一个序列，使用指定的排序谓词和哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`、 排序谓词，默认值和默认哈希函数。 你可以使用它来使一个枚举器，使用默认的排序谓词和哈希函数所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使所描述的枚举，使用指定排序谓词和默认哈希的函数的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使所描述的枚举，使用指定的排序谓词和哈希函数的另一个序列的副本的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
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
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)