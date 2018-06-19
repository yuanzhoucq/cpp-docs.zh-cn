---
title: 'queue:: pop (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::pop
dev_langs:
- C++
helpviewer_keywords:
- pop member [STL/CLR]
ms.assetid: 38f6c03b-e8f8-4663-b3d6-18314cdc8e7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0d3ab61f5108db8fc8c0d05262be4800c1329224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162648"
---
# <a name="queuepop-stlclr"></a>queue::pop (STL/CLR)
移除的最后一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
void pop();  
```  
  
## <a name="remarks"></a>备注  
 成员函数删除受控序列，必须为非空的最后一个元素。 你可以使用它将在后面的一个元素缩短队列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_pop.cpp   
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
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
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
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)