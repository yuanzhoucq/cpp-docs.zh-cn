---
title: "is_error_condition_enum 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_error_condition_enum
- system_error/std::is_error_condition_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 15
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 316e375554d80bfa58dfba537e5c36a881028a20
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum 类
表示测试 [error_condition](../standard-library/error-condition-class.md) 枚举的类型谓词。  
  
## <a name="syntax"></a>语法  
  
```
template <_Enum>
class is_error_condition_enum;
```  
  
## <a name="remarks"></a>备注  
 如果类型 `_Enum` 是一个适合存储在类型 `error_condition` 的对象中的枚举值，则此[类型谓词](../standard-library/type-traits.md)的实例为 true。  
  
 允许将专用化添加到此类型，以获得用户定义类型。  
  
## <a name="requirements"></a>要求  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)




