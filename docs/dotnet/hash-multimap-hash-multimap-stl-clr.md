---
title: "hash_multimap::hash_multimap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::hash_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multimap 成员 [STL/CLR]"
ms.assetid: a1d576a7-5dc7-4ad9-abef-ee7a13caaec3
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multimap::hash_multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
hash_multimap();  
explicit hash_multimap(key_compare^ pred);  
hash_multimap(key_compare^ pred, hasher^ hashfn);  
hash_multimap(hash_multimap<Key, Mapped>% right);  
hash_multimap(hash_multimap<Key, Mapped>^ right);  
template<typename InIter>  
    hash_multimaphash_multimap(InIter first, InIter last);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_multimap();`  
  
 初始化控制序列没有元素，并且默认排序谓词使用默认 `key_compare()`和哈希函数。  使用它来指定空的初始序列，使用控制默认排序和哈希函数。  
  
 构造函数：  
  
 `explicit hash_multimap(key_compare^ pred);`  
  
 初始化控制序列没有元素，并且排序谓词使用默认 `pred`和哈希函数。  使用它来指定空的初始序列，使用控制指定排序和默认的哈希函数。  
  
 构造函数：  
  
 `hash_multimap(key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列没有元素，并且排序谓词使用 `pred`和哈希函数`hashfn`。  使用它来指定空的初始序列，使用控制指定排序和哈希函数。  
  
 构造函数：  
  
 `hash_multimap(hash_multimap<Key, Mapped>% right);`  
  
 初始化控制序列，使用序列 `[``right``.`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``.`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`，使用默认排序谓词，和默认哈希函数。  可以使用它来指定初始化的控制序列，该序列是由该hash\_multimap对象`right`控制序列的副本并使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multimap(hash_multimap<Key, Mapped>^ right);`  
  
 初始化控制序列，使用序列 `[``right``->`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``->`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`，使用默认排序谓词，和默认哈希函数。  可以使用它来指定初始化的控制序列，该序列是由该hash\_multimap对象`right`控制序列的副本并使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`，使用默认排序谓词，和默认哈希函数。  使用会使控制序列复制另一个序列，其中包含默认排序谓词和哈希函数中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`，使用排序谓词 `pred`，和默认哈希函数。  使用会使控制序列复制另一个序列，其中包含指定排序谓词和默认哈希函数中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列，使用序列 `[``first``,` `last``)`,使用排序谓词 `pred`, 和指定哈希函数`hashfn`.  使用会使控制序列复制另一个序列，其中包含指定排序谓词和哈希函数中。  
  
 构造函数：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并默认排序谓词和具有默认哈希函数。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并默认排序谓词`pred`和具有默认哈希函数。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含指定排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并排序谓词`pred`和具认哈希函数`hashfn`。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含指定排序谓词和哈希函数。  
  
## 示例  
  
```  
// cliext_hash_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
// construct an empty container   
    Myhash_multimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multimap c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multimap c3(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multimap c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3);   
    for each (Myhash_multimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multimap c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multimap c7(c4);   
    for each (Myhash_multimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_multimap c8(%c3);   
    for each (Myhash_multimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::generic\_container](../dotnet/hash-multimap-generic-container-stl-clr.md)   
 [hash\_multimap::operator\=](../dotnet/hash-multimap-operator-assign-stl-clr.md)