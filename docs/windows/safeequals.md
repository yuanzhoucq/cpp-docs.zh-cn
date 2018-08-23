---
title: SafeEquals |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b0c2bb91f21b48554ca523a3523e82eee09d2fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600578"
---
# <a name="safeequals"></a>SafeEquals

比较两个数字，以确定它们是否相等。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

[in]*t*  
要比较的第一个数字。 其类型必须为 T。

[in]*u*  
要比较的第二个数字。 其类型必须为 U。

## <a name="return-value"></a>返回值

**true**如果*t*并*u*相等; 否则为**false**。

## <a name="remarks"></a>备注

该方法增强了`==`因为**SafeEquals** ，您可以比较两个不同类型的数字。

此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单一比较[SafeInt 类](../windows/safeint-class.md)。

> [!NOTE]
> 此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。

有关模板类型 T 和 U 的详细信息，请参阅[SafeInt 函数](../windows/safeint-functions.md)。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 函数](../windows/safeint-functions.md)  
[SafeInt 库](../windows/safeint-library.md)  
[SafeInt 类](../windows/safeint-class.md)  
[SafeNotEquals](../windows/safenotequals.md)