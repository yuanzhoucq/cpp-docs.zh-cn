---
title: 'set:: count (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::Count
dev_langs:
- C++
helpviewer_keywords:
- count member [STL/CLR]
ms.assetid: 78855f8c-3de5-4d3e-800b-0bbea5e829dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4eec1e7eaa68bf7273855a4f77e09280e2737a93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="setcount-stlclr"></a>set::count (STL/CLR)
查找与指定键匹配的元素数。  
  
## <a name="syntax"></a>语法  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 成员函数返回拥有等效顺序与控制序列中的元素数目`key`。 你可以使用它来确定当前受控序列中与指定的键匹配的元素的数目。  
  
## <a name="example"></a>示例  
  
```  
// cliext_set_count.cpp   
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
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)