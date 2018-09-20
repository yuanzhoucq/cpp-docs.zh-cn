---
title: 'Hstringreference:: Operator ！ = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 996ead81a72fb3cc58544576059a8347972e2a6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429037"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= 运算符

指示两个参数是否不相等。

## <a name="syntax"></a>语法

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较的第一个参数。 *lhs*可以是**HStringReference**对象或 HSTRING 句柄。

*rhs*<br/>
要比较的第二个参数。  *rhs*可以是**HStringReference**对象或 HSTRING 句柄。

## <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数是否不相等; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)