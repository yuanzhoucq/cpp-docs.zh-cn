---
title: 'list:: splice (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::splice
dev_langs:
- C++
helpviewer_keywords:
- splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0c92faf6a4ec84e6ed65c58d02337038398d37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135945"
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch 节点之间的链接。  
  
## <a name="syntax"></a>语法  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要拼接的范围开始处。  
  
 last  
 要拼接的范围的末尾。  
  
 右  
 要从中进行拼接的容器。  
  
 其中  
 Splice 之前容器中的位置。  
  
## <a name="remarks"></a>备注  
 第一个成员函数将插入所控制序列`right`指向的受控序列中的元素之前`where`。 它还会删除 `right` 中的所有元素。 (`%right`必须不等于`this`。)你可以使用它要拼接到另一个列表的所有。  
  
 第二个成员函数中移除的元素指向`first`中控制的序列`right`并将其插入之前由指向受控序列中的元素`where`。 (如果`where` `==` `first` `||` `where` `== ++first`，不会发生更改。)你可以使用它要拼接到另一个列表的单一元素。  
  
 第三个成员函数将插入指定的子范围 [`first`， `last`) 控制的序列从`right`指向的受控序列中的元素之前`where`。 它还会删除由 `right` 控制的序列中的原始子范围。 (如果`right` `==` `this`，范围 [`first`， `last`) 不能包含指向的元素`where`。)你可以使用它要拼接到另一个列表中的零个或多个元素的子序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list:: insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)