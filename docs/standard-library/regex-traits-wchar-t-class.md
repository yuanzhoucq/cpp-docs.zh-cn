---
title: "regex_traits&lt;wchar_t&gt; 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- regex/std::regex_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- regex_traits<wchar_t> class
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77a754726580401424b3b9194667e8f2558f7cd6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="regextraitsltwchartgt-class"></a>regex_traits&lt;wchar_t&gt; 类
用于 wchar_t 的 regex_traits 的专用化。  
  
## <a name="syntax"></a>语法  
  
```  
template <>  
class regex_traits<wchar_t>  
```  
  
## <a name="remarks"></a>备注  
 此类是类型为 `wchar_t` 的元素的 [regex_traits](../standard-library/regex-traits-class.md) 模板类的显式专用化（以便它可以充分利用操作此类型对象的库函数）。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<regex 1>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
[\<regex>](../standard-library/regex.md)  
[regex_constants 类](../standard-library/regex-constants-class.md)  
[regex_error 类](../standard-library/regex-error-class.md)  
[\<regex> functions](../standard-library/regex-functions.md)  
[regex_iterator 类](../standard-library/regex-iterator-class.md)  
[\<regex> operators](../standard-library/regex-operators.md)  
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)  
[regex_traits 类](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  
