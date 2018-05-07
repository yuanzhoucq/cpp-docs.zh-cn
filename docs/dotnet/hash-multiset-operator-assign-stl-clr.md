---
title: hash_multiset::operator = (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 1b4d5b0a-f10f-42f8-b67b-76af51c66baf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2414547feb4609051def50bc5b0b20378ae493e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultisetoperator-stlclr"></a>hash_multiset::operator= (STL/CLR)
替换受控序列。  
  
## <a name="syntax"></a>语法  
  
```  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 用于复制的容器。  
  
## <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
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
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)