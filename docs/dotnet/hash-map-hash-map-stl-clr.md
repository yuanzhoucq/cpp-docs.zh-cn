---
title: "hash_map::hash_map (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map 成员 [STL/CLR]"
ms.assetid: d65eb3fa-4bf9-4186-95f8-5517c90ef1fa
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::hash_map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
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
  
#### 参数  
 首先  
 插入范围的开头。  
  
 hashfn  
 映射到键的哈希函数存储桶。  
  
 last  
 插入的范围末尾。  
  
 pred  
 排序规则序列的谓词。  
  
 right  
 插入的对象或值范围。  
  
## 备注  
 构造函数：  
  
 `hash_map();`  
  
 初始化控制序列没有元素，并且默认排序谓词使用默认 `key_compare()`和哈希函数。  使用它来指定空的初始序列，以控制默认排序谓词和哈希函数中。  
  
 构造函数：  
  
 `explicit hash_map(key_compare^ pred);`  
  
 初始化控制序列没有元素，与顺序的谓词使用默认 `pred`和哈希函数。  使用该指定一个空控件，使用初始序列指定顺序的谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_map(key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列没有元素，与顺序的谓词使用哈希函数 `pred`和 `hashfn`。  使用该指定一个空控件，使用初始序列指定顺序的谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>% right);`  
  
 初始化控制序列的序列 `[``right``.``(),` `right``.`[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)`())`，而默认排序谓词和具有默认哈希函数。  将它指定为复制由其中的顺序控制默认 hash\_map `right`对象排序，谓词和哈希函数的初始序列控制。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>^ right);`  
  
 初始化控制序列的序列 `[``right``->``(),` `right``->`[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)`())`，而默认排序谓词和具有默认哈希函数。  将它指定为复制由其中的顺序控制默认 hash\_map `right`对象排序，谓词和哈希函数的初始序列控制。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last);`  
  
 初始化控制序列的序列 `[``first``,` `last``)`，其默认排序谓词和具有默认哈希函数。  使用会使控制序列复制另一个序列，其中包含默认排序谓词和哈希函数中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列的序列 `[``first``,` `last``)`，其顺序的谓词使用默认 `pred`和哈希函数。  使用会使控制序列复制其他序列，具有指定顺序的谓词和默认哈希函数。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列的序列 `[``first``,` `last``)`，其顺序的谓词使用哈希函数 `pred`和 `hashfn`。  使用会使控制序列复制其他序列，具有指定顺序的谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列的枚举数指定的 `right`序列，并默认排序谓词和具有默认哈希函数。  使用会使控制枚举数的序列描述复制另一个序列，其中包含默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列的枚举数指定的序列排序的谓词，`right`与 `pred`和与默认哈希函数。  使用会使控制枚举数的序列描述复制其他序列，具有指定顺序的谓词以及默认的哈希函数。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列的枚举数的序列排序的谓词指定 `right`，与 `pred`和与哈希函数 `hashfn`。  使用会使控制枚举数的序列描述复制其他序列，具有指定顺序的谓词和哈希函数的。  
  
## 示例  
  
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
 **页眉：** \<cliext\/hash\_map\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::generic\_container](../dotnet/hash-map-generic-container-stl-clr.md)   
 [hash\_map::operator\=](../dotnet/hash-map-operator-assign-stl-clr.md)