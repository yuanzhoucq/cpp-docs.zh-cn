---
title: "运算符 = = （队列） (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::operator==
dev_langs: C++
helpviewer_keywords: operator== member [STL/CLR]
ms.assetid: ad183c61-a24a-4851-aac7-2a47a1371ec2
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07e674dff56bc64f8b549b7f5d541032d1eaf310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="operator-queue-stlclr"></a>operator== (queue) (STL/CLR)
队列相等比较。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator==(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>参数  
 左  
 要比较的左容器。  
  
 右  
 要比较的右容器。  
  
## <a name="remarks"></a>备注  
 运算符函数，则返回 true，才由控制序列`left`和`right`具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 用于测试是否`left`进行排序相同`right`两个队列时由元素的比较的元素。  
  
## <a name="example"></a>示例  
  
```  
// cliext_queue_operator_eq.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/队列 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [队列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [运算符 ！ = （队列） (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [运算符\<（队列） (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [运算符 > = （队列） (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [运算符 > （队列） (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)