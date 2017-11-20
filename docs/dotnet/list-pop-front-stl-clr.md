---
title: "list:: pop_front (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::pop_front
dev_langs: C++
helpviewer_keywords: pop_front member [STL/CLR]
ms.assetid: 6a0bad42-6796-41d9-a3e9-1488b3882574
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa9df1ea52b525d00aa77478f6fcbe1f3e29b29c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="listpopfront-stlclr"></a>list::pop_front (STL/CLR)
移除的第一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
void pop_front();  
```  
  
## <a name="remarks"></a>备注  
 成员函数删除必须为非空的受控序列的第一个元素。 你可以使用它来缩短在前面的一个元素的列表。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)   
 [list:: push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)   
 [list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)