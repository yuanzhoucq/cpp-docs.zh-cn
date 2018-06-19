---
title: 'vector:: insert (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 06b4b5c6385d92e1fb03d05e96716075a5e2f6f3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172321"
---
# <a name="vectorinsert-stlclr"></a>vector::insert (STL/CLR)
将元素添加的指定位置。  
  
## <a name="syntax"></a>语法  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 count  
 要插入的元素数。  
  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 右  
 要插入的枚举。  
  
 val  
 要插入的元素的值。  
  
 其中  
 要在其前插入容器中的何处。  
  
## <a name="remarks"></a>备注  
 每个成员函数插入的指向的元素之前`where`剩余操作数到受控序列中指定一个序列。  
  
 第一个成员函数将具有值的元素插入`val`返回迭代器，它指定新插入的元素。 你可以使用它来插入单个元素之前指定迭代器的位置。  
  
 第二个成员函数插入 `count` 元素的重复元素，值为 `val`。 用于插入零个或多个由连续的元素是相同的值的所有副本。  
  
 如果 `InIt` 是整数类型，则第三个成员函数的行为与 `insert(where, (size_type)first, (value_type)last)` 相同。 否则，它还将序列插入 [`first`， `last`)。 用于插入零个或多个由连续的元素从另一个序列复制。  
  
 第四个成员函数将由序列插入`right`。 用于插入一个枚举器所描述的序列。  
  
 在插入单个元素时，元素副本的数目上呈线性之间插入点和最近序列末尾的元素数目。 （当将一个或多个元素插入序列的任意一端，没有元素副本会发生。）如果`InIt`作为输入的迭代器，第三个成员函数有效地执行每个序列中元素的单个插入。 否则为插入时`N`元素，元素副本的数目上呈线性`N`plus 之间插入点和最近序列末尾的元素数目。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)