---
title: 'hash_multiset:: insert (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: e7254f30-a514-4ddc-bf53-38aafbe9e8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 243c07eae12026115f12e042b9fbe49b97cdb1b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultisetinsert-stlclr"></a>hash_multiset::insert (STL/CLR)
添加元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 右  
 要插入的枚举。  
  
 val  
 要插入的密钥值。  
  
 其中  
 要插入 （仅提示） 的容器中的位置。  
  
## <a name="remarks"></a>备注  
 每个成员函数将插入剩余操作数指定的序列。  
  
 第一个成员函数将具有值的元素插入`val`，并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素。  
  
 第二个成员函数将具有值的元素插入`val`，使用`where`作为提示，（用于提高性能），并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素，这可能是靠近你知道的元素。  
  
 第三个成员函数将序列插入 [`first`， `last`)。 你可以使用它将从另一个序列复制的零个或多个元素。  
  
 第四个成员函数将由序列插入`right`。 用于插入一个枚举器所描述的序列。  
  
 每个元素插入受控序列中需要的元素数的对数成正比的时间。 插入可能发生在分期常量时间内，但是，给定一个提示，指示某个元素的插入点旁边。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)