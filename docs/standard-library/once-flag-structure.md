---
title: "once_flag 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: mutex/std::once_flag
dev_langs: C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc66f322490bc728ab6d25e185f6b8d4ce0f0179
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="onceflag-structure"></a>once_flag 结构
表示与模板函数 [call_once](../standard-library/mutex-functions.md#call_once) 结合使用的 `struct`，以确保即使出现多个执行线程，初始化代码只调用一次。  
  
## <a name="syntax"></a>语法  
  
struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };  
  
## <a name="remarks"></a>备注  
 `once_flag` `struct`具有默认构造函数。  
  
 可以创建 `once_flag` 类型的对象，但不能复制它们。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<互斥体 >  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



