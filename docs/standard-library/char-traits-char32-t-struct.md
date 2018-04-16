---
title: "char_traits&lt;char32_t&gt; 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d624cbeb797e5c81bb10d7ec8e532ce881cd700
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="chartraitsltchar32tgt-struct"></a>char_traits&lt;char32_t&gt; 结构
此结构是模板结构 **char_traits\<CharType>** 对 `char32_t` 类型的一个元素的专用化。  
  
## <a name="syntax"></a>语法  
  
```
template <>  
struct char_traits<char32_t>;
```  
  
## <a name="remarks"></a>备注  
 专用化允许结构利用库函数处理此 `char32_t` 类型的对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<string>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [\<string>](../standard-library/string.md)   
 [char_traits 结构](../standard-library/char-traits-struct.md)
