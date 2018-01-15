---
title: "SafeSubtract |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeSubtract
dev_langs: C++
helpviewer_keywords: SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b94d84e6a348b68258fc1b57c2e0ad9ad30e36d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="safesubtract"></a>SafeSubtract
防止溢出的方式的两个数字相减。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T, typename U>  
inline bool SafeSubtract (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 [in] `t`  
 减法运算中第一个数。 其类型必须为 T。  
  
 [in] `u`  
 要从中减去的数字`t`。 其类型必须为 U。  
  
 [out] `result`  
 参数其中`SafeSubtract`存储结果。  
  
## <a name="return-value"></a>返回值  
 `true`如果没有错误发生;`false`如果发生错误。  
  
## <a name="remarks"></a>备注  
 此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例专用于单个减法运算[SafeInt 类](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。  
  
 有关模板类型 T 和 U 的详细信息，请参阅[SafeInt 函数](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** safeint.h  
  
 **Namespace:** microsoft:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeAdd](../windows/safeadd.md)