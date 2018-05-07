---
title: 'multiset:: erase (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 3ff9fe2d-bf43-446a-bd3f-74550313a1d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bb5ac657a70d61f43245fb04bd4f49642e81a5f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="multiseterase-stlclr"></a>multiset::erase (STL/CLR)
移除指定位置处的元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要清除范围的起点。  
  
 密钥  
 要擦除的密钥值。  
  
 last  
 要清除范围的末尾。  
  
 其中  
 要清除的元素。  
  
## <a name="remarks"></a>备注  
 第一个成员函数删除指向的受控序列的元素`where`，并返回指定已移除的元素之外保留的第一个元素的迭代器或[multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`如果此类元素不存在。 用于删除单个元素。  
  
 第二个成员函数范围中移除受控序列的元素 [`first`， `last`)，并返回指定已移除，任何元素之外保留的第一个元素的迭代器或`end()`如果没有此类元素存在... 用于删除零个或多个由连续的元素。  
  
 第三个成员函数删除其键具有等效顺序受控任何的序列元素到`key`，并返回已移除的元素数的计数。 你可以使用它删除，用来计数与指定的键匹配的所有元素。  
  
 每个元素擦除需要受控序列中的元素数的对数成正比的时间。  
  
## <a name="example"></a>示例  
  
```  
// cliext_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Mymultiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)