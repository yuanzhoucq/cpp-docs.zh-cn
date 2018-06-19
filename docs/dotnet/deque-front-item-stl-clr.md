---
title: deque::front_item (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::front_item
dev_langs:
- C++
helpviewer_keywords:
- front_item member [STL/CLR]
ms.assetid: 6243e52d-47fb-45d8-ade8-70debd97887d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99b8d770bfb2dcbae4ce483fae446b66880d998c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109815"
---
# <a name="dequefrontitem-stlclr"></a>deque::front_item (STL/CLR)
访问第一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
property value_type front_item;  
```  
  
## <a name="remarks"></a>备注  
 属性访问必须为非空的受控序列的第一个元素。 你可以使用它来读取或写入的第一个元素，当你知道它存在。  
  
## <a name="example"></a>示例  
  
```  
// cliext_deque_front_item.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: back (STL/CLR)](../dotnet/deque-back-stl-clr.md)   
 [deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)   
 [deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)