---
title: 'Hstringreference:: Operator&lt;运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17acdca8af1250b1f88fa8a6858ffa1854f8ca8c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426401"
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: Operator&lt;运算符

指示第一个参数是否小于第二个参数。

## <a name="syntax"></a>语法

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()  
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是对引用**HStringReference**。

*rhs*<br/>
要比较的第二个参数。  *rhs*可以是对引用**HStringReference**。

## <a name="return-value"></a>返回值

**true**如果*lhs*参数是小于*rhs*参数; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)