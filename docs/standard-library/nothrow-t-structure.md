---
title: "nothrow_t 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nothrow_t
dev_langs: C++
helpviewer_keywords: nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9975df6ca866ce45a0e4859d19c6cfd6f3f96db2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 有关如何将 `std::nothrow_t` 用作函数参数的示例，请参阅[运算符 new](../standard-library/new-operators.md#op_new) 和[运算符 new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<new>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



