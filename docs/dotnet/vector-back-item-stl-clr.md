---
title: vector::back_item (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::back_item
dev_langs:
- C++
helpviewer_keywords:
- back_item member [STL/CLR]
ms.assetid: 9658ffa8-7bde-4242-9ed9-ca42be0d1433
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8a69eae367e809d6493a0d5aa975ce25bdf2dac5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166837"
---
# <a name="vectorbackitem-stlclr"></a>vector::back_item (STL/CLR)
访问最后一个元素。  
  
## <a name="syntax"></a>语法  
  
```  
property value_type back_item;  
```  
  
## <a name="remarks"></a>备注  
 属性访问受控序列，必须为非空的最后一个元素。 你可以使用它来读取或写入的最后一个元素，当你知道它存在。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_back_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: back (STL/CLR)](../dotnet/vector-back-stl-clr.md)   
 [vector:: front (STL/CLR)](../dotnet/vector-front-stl-clr.md)   
 [vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)