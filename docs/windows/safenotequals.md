---
title: SafeNotEquals |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeNotEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeNotEquals function
ms.assetid: 032e45a8-4159-4b55-b7cc-ecd27f4e4788
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61104cd55ed349131fc884951da77455aa9ca978
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889198"
---
# <a name="safenotequals"></a>SafeNotEquals
确定两个数字不相等。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T, typename U>  
inline bool SafeNotEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 [in] `t`  
 要比较的第一个数字。 其类型必须为 T。  
  
 [in] `u`  
 要比较的第二个数字。 其类型必须为 U。  
  
## <a name="return-value"></a>返回值  
 `true` 如果`t`和`u`不相等; 否则为`false`。  
  
## <a name="remarks"></a>备注  
 该方法增强了 `!=`，因为 `SafeNotEquals` 使您能够将两个不同类型的数字作比较。  
  
 此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单个比较运算[SafeInt 类](../windows/safeint-class.md)。  
  
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
 [SafeEquals](../windows/safeequals.md)