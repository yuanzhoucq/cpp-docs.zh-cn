---
title: "stack::assign (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::assign
dev_langs: C++
helpviewer_keywords: assign member [STL/CLR]
ms.assetid: 18cc35ad-23cf-4a5a-adae-d967dc5d6980
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 11214550141cc32c589ef090c48775390bc26627
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="stackassign-stlclr"></a>stack::assign (STL/CLR)
替换所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
void assign(stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要插入的容器适配器。  
  
## <a name="remarks"></a>备注  
 成员函数将指派`right.get_container()`到基础的容器。 你可以使用它来更改堆栈的全部内容。  
  
## <a name="example"></a>示例  
  
```  
// cliext_stack_assign.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mystack c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/堆栈 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)