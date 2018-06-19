---
title: 'set:: end (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::end
dev_langs:
- C++
helpviewer_keywords:
- end member [STL/CLR]
ms.assetid: 3fe66e73-5eb9-4972-8a07-01f2eb4d1ccb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: be579b09d55d099e142dff4aa14b9cd98da1678f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162470"
---
# <a name="setend-stlclr"></a>set::end (STL/CLR)
指定受控序列的末尾。  
  
## <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>备注  
 成员函数返回的双向迭代器，它指向刚超出受控序列的末尾。 用于获取指定的受控序列中; 末尾的迭代器其状态不更改如果更改了受控序列的长度。  
  
## <a name="example"></a>示例  
  
```  
// cliext_set_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)