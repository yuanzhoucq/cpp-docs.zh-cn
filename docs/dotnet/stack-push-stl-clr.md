---
title: 'stack:: push (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::push
dev_langs:
- C++
helpviewer_keywords:
- push member [STL/CLR]
ms.assetid: 60e5b076-c80f-4af0-a018-62cda7e081db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6236989d1bdcc9ee7f6705257c91e5509ae38878
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165384"
---
# <a name="stackpush-stlclr"></a>stack::push (STL/CLR)
添加新的最后一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>备注  
 成员函数将插入具有值的元素`val`受控序列的末尾。 你可以使用它要追加到堆栈的另一个元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_stack_push.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
 **标头：** \<cliext/堆栈 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)