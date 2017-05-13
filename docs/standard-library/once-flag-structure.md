---
title: "once_flag 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: a39919d3c1608d53edc6a75ecc3dd2e0ff504b1c
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="onceflag-structure"></a>once_flag 结构
表示与模板函数 [call_once](../standard-library/mutex-functions.md#call_once) 结合使用的 `struct`，以确保即使出现多个执行线程，初始化代码只调用一次。  
  
## <a name="syntax"></a>语法  
  
struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };  
  
## <a name="remarks"></a>备注  
 `once_flag``struct` 只有一个默认构造函数。  
  
 可以创建 `once_flag` 类型的对象，但不能复制它们。  
  
## <a name="requirements"></a>要求  
 **标头︰** \<互斥体 >  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




