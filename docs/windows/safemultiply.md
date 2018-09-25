---
title: SafeMultiply |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeMultiply
dev_langs:
- C++
helpviewer_keywords:
- SafeMultiply function
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0eb1b8b37737d1c0c36af28da9b0c656e26de7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396736"
---
# <a name="safemultiply"></a>SafeMultiply

将防止溢出的方式在一起的两个数字相乘。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]要相乘的第一个数字。 其类型必须为`T`。

*u*<br/>
[in]要相乘的第二个数字。 其类型必须为`U`。

*结果*<br/>
[out]参数位置**SafeMultiply**将结果存储。

## <a name="return-value"></a>返回值

**true**如果未发生错误;**false**如果发生错误。

## <a name="remarks"></a>备注

此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单个乘法运算[SafeInt 类](../windows/safeint-class.md)。

> [!NOTE]
> 此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。

有关模板类型的详细信息`T`并`U`，请参阅[SafeInt 函数](../windows/safeint-functions.md)。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 函数](../windows/safeint-functions.md)<br/>
[SafeInt 库](../windows/safeint-library.md)<br/>
[SafeInt 类](../windows/safeint-class.md)<br/>
[SafeDivide](../windows/safedivide.md)