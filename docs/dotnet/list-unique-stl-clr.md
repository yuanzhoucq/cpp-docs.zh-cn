---
title: 'list:: unique (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::unique
dev_langs:
- C++
helpviewer_keywords:
- unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5dbfab0fb53a4ca11128d01e7b32060c6428549
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
删除通过了指定测试的相邻元素。  
  
## <a name="syntax"></a>语法  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>参数  
 pred  
 用于元素对比较器。  
  
## <a name="remarks"></a>备注  
 从受控序列 （擦除） 中移除第一个成员函数将进行比较的每个元素等于其前面的元素-如果元素`X`元素前面`Y`和`X == Y`，成员函数删除`Y`。 你使用它删除的每个的相邻元素的子序列的所有只保留一个副本该比较等。 请注意，如果受控的序列进行排序，如通过调用[list:: sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`，成员函数将只有元素留下唯一值。 （由此而得名）。  
  
 第二个成员函数行为与第一个相同，只不过它会删除每个元素`Y`以下元素`X`为其`pred(X, Y)`。 用于删除的每个满足谓词的函数或你指定的委托的相邻元素的子序列的所有只保留一个副本。 请注意，如果受控的序列进行排序，如通过调用`sort(pred)`，成员函数离开没有等效的顺序与任何其他元素的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list:: remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)