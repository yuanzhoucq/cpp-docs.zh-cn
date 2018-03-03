---
title: "vector:: resize (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3b4fbc196f9e4ca14ee8d8e744da380e08ec4d8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vectorresize-stlclr"></a>vector::resize (STL/CLR)
更改元素的数目。  
  
## <a name="syntax"></a>语法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>参数  
 new_size  
 受控序列的新大小。  
  
 val  
 填充元素的值。  
  
## <a name="remarks"></a>备注  
 这两个成员函数确保[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()`之后返回`new_size`。 如果它必须使受控序列更长，则第一个成员函数追加具有值 `value_type()` 的元素，而第二个成员函数追加具有值 `val` 的元素。 若要使较短的受控的序列，这两个成员函数，有效地擦除的最后一个元素[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size`时间。 用于确保受控的序列具有大小`new_size`、 修剪或填充当前的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)   
 [vector:: erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)