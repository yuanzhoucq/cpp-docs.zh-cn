---
title: "queue:: queue (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::queue
dev_langs: C++
helpviewer_keywords: queue member [STL/CLR]
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6c4b24ad40bf19b7a20aafcfa2d02fb6490fed1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="queuequeue-stlclr"></a>queue::queue (STL/CLR)
构造容器适配器对象。  
  
## <a name="syntax"></a>语法  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的对象。  
  
 包装  
 要使用的已包装的容器。  
  
## <a name="remarks"></a>备注  
 构造函数：  
  
 `queue();`  
  
 创建一个空的已包装的容器。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `queue(queue<Value, Container>% right);`  
  
 创建一个已包装的容器，它是一份`right.get_container()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`right`。  
  
 构造函数：  
  
 `queue(queue<Value, Container>^ right);`  
  
 创建一个已包装的容器，它是一份`right->get_container()`。 用于指定是通过对队列对象控制的序列的副本的初始受控的序列`*right`。  
  
 构造函数：  
  
 `explicit queue(container_type wrapped);`  
  
 使用现有容器`wrapped`作为已包装的容器。 你可以使用它来构造一个队列从现有容器。  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)   
 [queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)