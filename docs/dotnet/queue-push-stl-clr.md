---
title: "queue:: push (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::push
dev_langs: C++
helpviewer_keywords: push member [STL/CLR]
ms.assetid: 97cf1f98-d4c4-417f-b57a-89cdd351ef65
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86fd84c8f5e50b08ae5535703d808e9b690d4521
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="queuepush-stlclr"></a>queue::push (STL/CLR)
添加新的最后一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>备注  
 成员函数添加一个带有值元素`val`队列的末尾。 用于将元素追加到队列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_push.cpp   
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
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)