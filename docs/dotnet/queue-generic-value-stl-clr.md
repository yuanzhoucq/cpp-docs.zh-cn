---
title: "queue::generic_value (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::generic_value
dev_langs: C++
helpviewer_keywords: generic_value member [STL/CLR]
ms.assetid: 5efd9812-6b4d-4e59-b8e8-c4975ae61667
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4e3dbf57b9dd3535a430066cfd4c0eeda26ef92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="queuegenericvalue-stlclr"></a>queue::generic_value (STL/CLR)
使用容器的泛型接口具有的元素的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。 (`GValue`是`value_type`或`value_type^`如果`value_type`是 ref 类型。)  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)