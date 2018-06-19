---
title: 'queue:: value_type (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: f1abde03-982c-4aaf-91a6-cc613df9690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3faec40fb0e8c58de03b3fa24d75459a6ac208ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160610"
---
# <a name="queuevaluetype-stlclr"></a>queue::value_type (STL/CLR)
元素的类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>备注  
 该类型是模板参数 `Value` 的同义词。  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Myqueue::value_type val = c1.front();   
  
        System::Console::Write(" {0}", val);   
        }   
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
  
## <a name="see-also"></a>请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)   
 [queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)