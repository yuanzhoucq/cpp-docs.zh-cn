---
title: "map:: insert (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 599c702e-7db0-45b8-8247-4ff041a3639c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 495a3e80e28ea70f1784f12ee9750050847e6e2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mapinsert-stlclr"></a>map::insert (STL/CLR)
添加元素。  
  
## <a name="syntax"></a>语法  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 第一个成员函数插入具有值的元素致力于`val`，并返回一对值`X`。 如果`X.second`为 true，`X.first`指定新插入的元素; 否则为`X.first`指定具有等效的元素排序已经存在，并且插入任何新元素。 你可以使用它来插入单个元素。  
  
 第二个成员函数将具有值的元素插入`val`，使用`where`作为提示，（用于提高性能），并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素，这可能是靠近你知道的元素。  
  
 第三个成员函数将序列插入 [`first`， `last`)。 你可以使用它将从另一个序列复制的零个或多个元素。  
  
 第四个成员函数将由序列插入`right`。 用于插入一个枚举器所描述的序列。  
  
 每个元素插入受控序列中需要的元素数的对数成正比的时间。 插入可能发生在分期常量时间内，但是，给定一个提示，指示某个元素的插入点旁边。  
  
## <a name="example"></a>示例  
  
```  
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [[x 24] True]  
insert([L'b' 2]) = [[b 2] False]  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [map (STL/CLR)](../dotnet/map-stl-clr.md)