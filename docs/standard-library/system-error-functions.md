---
title: "&lt;system_error&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 43098f6f9276c9a66aaa7a30c95a6696e33f8429
ms.lasthandoff: 02/24/2017

---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函数
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="a-namegenericcategorya--genericcategory"></a><a name="generic_category"></a>generic_category  
 表示一般错误的类别。  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>备注  
 `generic_categor`y 对象是 [error_category](../standard-library/error-category-class.md) 的实现。  
  
##  <a name="a-namemakeerrorcodea--makeerrorcode"></a><a name="make_error_code"></a>make_error_code  
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
  
##  <a name="a-namemakeerrorconditiona--makeerrorcondition"></a><a name="make_error_condition"></a>make_error_condition  
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
  
##  <a name="a-namesystemcategorya--systemcategory"></a><a name="system_category"></a>  system_category  
 表示因低级别系统溢出而引起的错误类别。  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>备注  
 `system_categor`y 对象是 [error_category](../standard-library/error-category-class.md) 的实现。  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)




