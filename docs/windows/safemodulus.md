---
title: SafeModulus |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec263f2da2374c66c7333a57f69ff6afbf0553fb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013631"
---
# <a name="safemodulus"></a>SafeModulus
执行取模运算对两个数字。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>参数  
 [in]*t*  
 除数。 其类型必须为`T`。  
  
 [in]*u*  
 被除数。 其类型必须为`U`。  
  
 [out]*结果*  
 参数位置**SafeModulus**将结果存储。  
  
## <a name="return-value"></a>返回值  
 **true**如果未发生错误;**false**如果发生错误。  
  
## <a name="remarks"></a>备注  
 此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单个取模运算[SafeInt 类](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。  
  
 有关模板类型的详细信息`T`并`U`，请参阅[SafeInt 函数](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** microsoft:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)