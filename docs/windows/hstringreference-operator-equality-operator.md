---
title: 'Hstringreference:: Operator = = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b07df3dc50704a87883e1a387fe9c842c1732b54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610528"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== 运算符

指示两个参数是否相等。

## <a name="syntax"></a>语法

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>参数

*lhs*  
要比较的第一个参数。 *lhs*可以是**HStringReference**对象或 HSTRING 句柄。

*rhs*  
要比较的第二个参数。  *rhs*可以是**HStringReference**对象或 HSTRING 句柄。

## <a name="return-value"></a>返回值

**true**如果*lhs*并*rhs*参数不相等; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)