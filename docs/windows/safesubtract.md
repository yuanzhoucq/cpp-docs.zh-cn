---
title: SafeSubtract |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac6968a688c50ad665e8b28a883eaf62255aaf28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700105"
---
# <a name="safesubtract"></a>SafeSubtract

防止溢出的方式的两个数字相减。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>参数

*t*<br/>
[in]该减法运算中的第一号。 其类型必须为`T`。

*u*<br/>
[in]要从中减去的数字*t*。 其类型必须为`U`。

*结果*<br/>
[out]参数位置**SafeSubtract**将结果存储。

## <a name="return-value"></a>返回值

**true**如果未发生错误;**false**如果发生错误。

## <a name="remarks"></a>备注

此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单个减法运算[SafeInt 类](../windows/safeint-class.md)。

> [!NOTE]
> 此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。

有关模板类型的详细信息`T`并`U`，请参阅[SafeInt 函数](../windows/safeint-functions.md)。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 函数](../windows/safeint-functions.md)  
[SafeInt 库](../windows/safeint-library.md)  
[SafeInt 类](../windows/safeint-class.md)  
[SafeAdd](../windows/safeadd.md)