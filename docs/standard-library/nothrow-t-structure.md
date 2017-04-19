---
title: "nothrow_t 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: b490cccf048b5d5b9be53508331cba89e66c952f
ms.lasthandoff: 02/24/2017

---
# <a name="nothrowt-structure"></a>nothrow_t 结构
该结构用作运算符 new 的函数参数，指示函数应返回一个 null 指针来报告分配失败，而不是引发异常。  
  
## <a name="syntax"></a>语法  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>备注  
 该结构可帮助编译器选择正确版本的构造函数。 [nothrow](../standard-library/new-functions.md#nothrow) 是 `std::nothrow_t` 类型的对象的同义词。  
  
## <a name="example"></a>示例  
 有关如何将 `std::nothrow_t` 用作函数参数的示例，请参阅[运算符 new](../standard-library/new-operators.md#operator_new) 和[运算符 new&#91;&#93;](../standard-library/new-operators.md#operator_new_arr)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<new>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




