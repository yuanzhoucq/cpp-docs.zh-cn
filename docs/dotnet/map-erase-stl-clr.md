---
title: "map:: erase (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: a8fc88dd-a726-4a5b-bdf2-87743e98e687
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 320be2b045ed128885a581b995f1e3979baea491
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="maperase-stlclr"></a>map::erase (STL/CLR)
移除指定位置处的元素。  
  
## <a name="syntax"></a>语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
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
 第一个成员函数删除指向的受控序列的元素`where`，并返回指定已移除的元素之外保留的第一个元素的迭代器或[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()`如果此类元素不存在。 用于删除单个元素。  
  
 第二个成员函数范围中移除受控序列的元素 [`first`， `last`)，并返回指定已移除，任何元素之外保留的第一个元素的迭代器或`end()`如果没有此类元素存在... 用于删除零个或多个由连续的元素。  
  
 第三个成员函数删除其键具有等效顺序受控任何的序列元素到`key`，并返回已移除的元素数的计数。 你可以使用它删除，用来计数与指定的键匹配的所有元素。  
  
 每个元素擦除需要受控序列中的元素数的对数成正比的时间。  
  
## <a name="example"></a>示例  
  
```  
// cliext_map_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    cliext::map<wchar_t, int> c1;   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::map<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [映射 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)