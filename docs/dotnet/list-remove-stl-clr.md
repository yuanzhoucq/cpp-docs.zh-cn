---
title: "list:: remove (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::remove
dev_langs: C++
helpviewer_keywords: remove member [STL/CLR]
ms.assetid: eaf598ee-e8fd-4cc0-be69-ca81a80e1d51
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 19534e3b2552c8226dee72862f8f9fdfb1709ce7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="listremove-stlclr"></a>list::remove (STL/CLR)
删除具有指定值的元素。  
  
## <a name="syntax"></a>语法  
  
```  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>参数  
 val  
 要移除的元素的值。  
  
## <a name="remarks"></a>备注  
 成员函数将为其受控序列中移除一个元素`((System::Object^)val)->Equals((System::Object^)x)`为 true （如果有）。 你可以使用它来擦除具有指定值的任意元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_remove.cpp   
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
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a c  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list:: erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)