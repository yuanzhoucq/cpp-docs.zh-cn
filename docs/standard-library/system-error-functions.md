---
title: "&lt;system_error&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: bcc9ee1b015699ab0c44bb362bcf82bc0597eb22
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函数
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="generic_category"></a>generic_category  
 表示一般错误的类别。  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>备注  
 `generic_category`对象是实现的[error_category](../standard-library/error-category-class.md)。  
  
##  <a name="make_error_code"></a>make_error_code  
 创建错误代码对象。  
  
```
error_code make_error_code(generic_errno _Errno);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errno`|要存储在错误代码对象中的枚举值。|  
  
### <a name="return-value"></a>返回值  
 错误代码对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="make_error_condition"></a>make_error_condition  
 创建错误条件对象。  
  
```
error_condition make_error_condition(generic_errno _Errno);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errno`|要存储在错误条件对象中的枚举值。|  
  
### <a name="return-value"></a>返回值  
 错误条件对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="system_category"></a>  system_category  
 表示因低级别系统溢出而引起的错误类别。  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>备注  
 `system_category`对象是实现的[error_category](../standard-library/error-category-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)




