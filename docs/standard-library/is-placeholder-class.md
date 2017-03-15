---
title: "is_placeholder 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_placeholder
- std::is_placeholder
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: a3624a752a500410ad906ba43a6c65310ba1cb41
ms.lasthandoff: 02/24/2017

---
# <a name="isplaceholder-class"></a>is_placeholder 类
测试类型是否为占位符。  
  
## <a name="syntax"></a>语法  
  
struct is_placeholder {  
   static const int value;  
   };  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 不是占位符，则常量值 `value` 为 0；否则，其值为其所绑定的函数调用参数的位置。 使用它来确定第 N 个占位符 `_N` 的值 `N`。  
  
## <a name="example"></a>示例  
  
```cpp  
// std__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}  
```  
  
```Output  
0  
3  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [_1 对象](../standard-library/1-object.md)


