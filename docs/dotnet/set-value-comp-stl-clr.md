---
title: "set:: value_comp (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::value_comp
dev_langs: C++
helpviewer_keywords: value_comp member [STL/CLR]
ms.assetid: 3b7e469d-ca73-415b-bd20-24968c51107c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3383634c38db8d4e6e6ee0548207c0ab189ad5ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setvaluecomp-stlclr"></a>set::value_comp (STL/CLR)
将复制两个元素值的排序委托。  
  
## <a name="syntax"></a>语法  
  
```  
value_compare^ value_comp();  
```  
  
## <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 使用两个元素值进行比较。  
  
## <a name="example"></a>示例  
  
```  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set:: value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)   
 [set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)