---
title: "char_traits&lt;char16_t&gt;结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
dev_langs: C++
helpviewer_keywords: char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 245ce0febf1a19e0bbb93c5d72584b26e23f6dfc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;char16_t&gt; 结构
此结构是模板结构 **char_traits\<CharType>** 对 `char16_t` 类型的一个元素的专用化。  
  
## <a name="syntax"></a>语法  
  
```
template <>  
struct char_traits<char16_t>;
```  
  
## <a name="remarks"></a>备注  
 专用化允许结构利用库函数处理 `char16_t` 类型的对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<string>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [\<string>](../standard-library/string.md)   
 [char_traits 结构](../standard-library/char-traits-struct.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



