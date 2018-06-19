---
title: 'deque:: resize (STL/CLR) |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c83f3c57-38b3-4706-a124-59bafbf88484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0d7e68fa1a58e70d4b414f81ca826e632c8706bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108876"
---
# <a name="dequeresize-stlclr"></a>deque::resize (STL/CLR)
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
 这两个成员函数确保[deque:: size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `()`之后返回`new_size`。 如果它必须使受控序列更长，则第一个成员函数追加具有值 `value_type()` 的元素，而第二个成员函数追加具有值 `val` 的元素。 若要使较短的受控的序列，这两个成员函数，有效地擦除的最后一个元素[deque:: size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() -` `new_size`时间。 用于确保受控的序列具有大小`new_size`、 修剪或填充当前的受控的序列。  
  
## <a name="example"></a>示例  
  
```  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
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
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)   
 [deque:: erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)   
 [deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)