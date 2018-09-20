---
title: SafeCast |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65794dafe5e45cbd4c0e2a7eb49c34377009deee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392978"
---
# <a name="safecast"></a>SafeCast

将转换为一种类型的另一种类型的数量。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>参数

*From*<br/>
[in]要转换的源数字。 其类型必须为`T`。

*若要*<br/>
[out]对新的数字类型的引用。 其类型必须为`U`。

## <a name="return-value"></a>返回值

**true**如果未发生错误;**false**如果发生错误。

## <a name="remarks"></a>备注

此方法属于[SafeInt 库](../windows/safeint-library.md)专为单一的强制转换操作而无需创建的实例并[SafeInt 类](../windows/safeint-class.md)。

> [!NOTE]
> 必须保护单个操作时，应仅使用此方法。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。

有关模板类型 T 和 U 的详细信息，请参阅[SafeInt 函数](../windows/safeint-functions.md)。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 函数](../windows/safeint-functions.md)<br/>
[SafeInt 库](../windows/safeint-library.md)<br/>
[SafeInt 类](../windows/safeint-class.md)