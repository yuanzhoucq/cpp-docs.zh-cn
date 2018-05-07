---
title: 'hash_map:: upper_bound (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- upper_bound member [STL/CLR]
ms.assetid: f83e88b4-e15e-49d5-90e4-cf7360c27c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 90253f383c89ff3f74dbc483cae027cc3325ad87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="hashmapupperbound-stlclr"></a>hash_map::upper_bound (STL/CLR)
查找与指定的键匹配的范围末尾。  
  
## <a name="syntax"></a>语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
## <a name="remarks"></a>备注  
 成员函数将确定最后一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，或者`X`为受控序列中的最后一个元素，它将返回[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; 否则它将返回指定以外的第一个元素的迭代器`X`. 用于当前与指定的键匹配的控制序列中查找的元素序列的末尾。  
  
## <a name="example"></a>示例  
  
```  
// cliext_hash_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_map::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: count (STL/CLR)](../dotnet/hash-map-count-stl-clr.md)   
 [hash_map:: equal_range (STL/CLR)](../dotnet/hash-map-equal-range-stl-clr.md)   
 [hash_map:: find (STL/CLR)](../dotnet/hash-map-find-stl-clr.md)   
 [hash_map::lower_bound (STL/CLR)](../dotnet/hash-map-lower-bound-stl-clr.md)