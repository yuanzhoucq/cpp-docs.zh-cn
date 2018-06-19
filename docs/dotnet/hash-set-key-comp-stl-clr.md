---
title: 'hash_set:: key_comp (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::key_comp
dev_langs:
- C++
helpviewer_keywords:
- key_comp member [STL/CLR]
ms.assetid: d5dc46c3-c2ee-4591-8f03-d8c9d3df0519
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4bb09f69fa6c4fd982433d51f5caf70bddb1a89
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126169"
---
# <a name="hashsetkeycomp-stlclr"></a>hash_set::key_comp (STL/CLR)
将复制为两个键排序的委托。  
  
## <a name="syntax"></a>语法  
  
```  
key_compare^key_comp();  
```  
  
## <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 用于比较两个键。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)   
 [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)