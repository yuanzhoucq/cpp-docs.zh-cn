---
title: SafeDivide |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0264fbd8df7f1dec5d20b40a67299cb4502b72aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="safedivide"></a>SafeDivide
使可防止被零除的方式的两个数字相除。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 [in] `t`  
 除数。 其类型必须为 T。  
  
 [in] `u`  
 被除数。 其类型必须为 U。  
  
 [out] `result`  
 参数其中`SafeDivide`存储结果。  
  
## <a name="return-value"></a>返回值  
 `true` 如果没有错误发生;`false`如果发生错误。  
  
## <a name="remarks"></a>备注  
 此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例专用于单个除法运算[SafeInt 类](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。  
  
 有关模板类型 T 和 U 的详细信息，请参阅[SafeInt 函数](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** microsoft:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)