---
title: SafeLessThan |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 499b621c804f13f6a56bc2ce9be0ba91ab824a48
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592395"
---
# <a name="safelessthan"></a>SafeLessThan

确定一个数是否小于另一个。

## <a name="syntax"></a>语法

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>参数

[in]*t*  
第一个数字。 其类型必须为`T`。

[in]*u*  
第二个号码。 其类型必须为`U`。

## <a name="return-value"></a>返回值

**true**如果*t*是小于*u*; 否则为**false**。

## <a name="remarks"></a>备注

此方法增强了的标准比较运算符，因为**SafeLessThan** ，您可以比较两个不同类型的数量。

此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单一比较[SafeInt 类](../windows/safeint-class.md)。

> [!NOTE]
> 此方法仅应在必须保护单个数学运算时使用。 如果有多个操作，则应使用`SafeInt`类而不是调用各个独立函数。

有关模板类型的详细信息`T`并`U`，请参阅[SafeInt 函数](../windows/safeint-functions.md)。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** microsoft:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 函数](../windows/safeint-functions.md)  
[SafeInt 库](../windows/safeint-library.md)  
[SafeInt 类](../windows/safeint-class.md)  
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)