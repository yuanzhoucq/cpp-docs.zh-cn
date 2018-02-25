---
title: "is_error_code_enum 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c7eb2de5bf2669f7833fffb8003ee1f0886c4bf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum 类
表示测试 [error_code](../standard-library/error-code-class.md) 枚举的类型谓词。  
  
## <a name="syntax"></a>语法  
  
```
template <_Enum>
class is_error_code_enum;
```  
  
## <a name="remarks"></a>备注  
 如果类型 `_Enum` 是一个适合存储在类型 `error_code` 的对象中的枚举值，则此[类型谓词](../standard-library/type-traits.md)的实例为 true。  
  
 允许将专用化添加到此类型，以获得用户定义类型。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)



