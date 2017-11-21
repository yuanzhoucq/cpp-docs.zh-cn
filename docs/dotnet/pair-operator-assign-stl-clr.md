---
title: "pair::operator = (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair::operator=
dev_langs: C++
helpviewer_keywords: operator= member [STL/CLR]
ms.assetid: b6228037-914e-4efa-8491-65dbb0e93f61
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa722f53c9ad76c32486d493db6d37e70ce12879
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pairoperator-stlclr"></a>pair::operator= (STL/CLR)
替换存储的值对。  
  
## <a name="syntax"></a>语法  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要复制的对。  
  
## <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用于使用存储对中值的副本替换存储的值对的`right`。  
  
## <a name="example"></a>示例  
  
```  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 3]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/实用工具 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [pair (STL/CLR)](../dotnet/pair-stl-clr.md)