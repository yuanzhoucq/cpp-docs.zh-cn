---
title: "bad_exception 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bad_exception
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7870c00b019718188b80a64e0102638deb76f588
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="badexception-class"></a>bad_exception 类
该类描述可从意外处理程序引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>备注  
 如果 `bad_exception` 包含在函数的引发列表中，则 [unexpected](../standard-library/exception-functions.md#unexpected) 将引发 `bad_exception`，而不是终止或调用使用 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 指定的其他函数。  
  
 **what** 返回的值是实现定义的 C 字符串。 无成员函数引发任何异常。  
  
 有关通过 `bad_exception` 类继承的成员列表，请参阅 [exception 类](../standard-library/exception-class.md)。  
  
## <a name="example"></a>示例  
 有关引发 `bad_exception` 的 [unexpected](../standard-library/exception-functions.md#unexpected) 的使用示例，请参阅 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<exception>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
[exception 类](../standard-library/exception-class.md)
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


