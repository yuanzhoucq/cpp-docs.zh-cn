---
title: "hash_multiset::hash_multiset (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::hash_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multiset 成员 [STL/CLR]"
ms.assetid: 1b224c60-b714-4ed5-9234-79b61b92a953
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::hash_multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### 参数  
 first  
 插入范围的开头。  
  
 hashfn  
 映射到键的哈希函数存储桶。  
  
 last  
 插入范围的末尾。  
  
 pred  
 排序规则序列的谓词。  
  
 right  
 要插入的对象或范围。  
  
## 备注  
 构造函数：  
  
 `hash_multiset();`  
  
 初始化控制没有元素的序列，并且默认排序谓词使用 `key_compare()`和默认哈希函数。  使用它来指定空的初始序列，使用控制默认排序和哈希函数。  
  
 构造函数：  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 初始化控制序列没有元素，并且排序谓词使用默认 `pred`和哈希函数。  使用它来指定空的初始序列，使用控制指定排序和默认的哈希函数。  
  
 构造函数：  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列没有元素，并且排序谓词使用 `pred`和哈希函数`hashfn`。  使用它来指定空的初始序列，使用控制指定排序和哈希函数。  
  
 构造函数：  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 初始化控制序列，使用序列 `[``right``.`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``.`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`，使用默认排序谓词，和默认哈希函数。  使用它来指定初始控制序列，该序列是由哈希多重集对象`right`控制的序列副本，使用默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 初始化控制序列，使用序列 `[``right``->`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``->`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`，使用默认排序谓词，和默认哈希函数。  使用它来指定初始控制序列，该序列是由哈希多重集对象`right`控制的序列副本，使用默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`，使用默认排序谓词，和默认哈希函数。  使用会使控制序列复制另一个序列，其中包含默认排序谓词和哈希函数中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`，使用排序谓词 `pred`，和默认哈希函数。  使用会使控制序列复制另一个序列，其中包含指定排序谓词和默认哈希函数中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`,使用排序谓词 `pred`, 和指定哈希函数`hashfn`.  使用会使控制序列复制另一个序列，其中包含指定排序谓词和哈希函数中。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并默认排序谓词和具有默认哈希函数。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并默认排序谓词`pred`和具有默认哈希函数。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含指定排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并排序谓词`pred`和具认哈希函数`hashfn`。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含指定排序谓词和哈希函数。  
  
## 示例  
  
```  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **c b a**  
 **a b c**  
 **a b c**  
 **c b a**  
 **a b c**  
 **a b c**  
 **c b a**  
 **a b c**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)