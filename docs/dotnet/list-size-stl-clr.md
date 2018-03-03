---
title: "list:: size (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::list::size
dev_langs:
- C++
helpviewer_keywords:
- size member [STL/CLR]
ms.assetid: 409e39fb-4468-44bb-b179-52c90e2fa293
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5a6081faf7034c158c53e36f930a3057168808a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="listsize-stlclr"></a>list::size (STL/CLR)
对元素数进行计数。  
  
## <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[list:: empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`。  
  
## <a name="example"></a>示例  
  
```  
// cliext_list_size.cpp   
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
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [列表 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)