---
title: 'Hstringreference:: Operator = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7045229cc15304a88253f97e1ad3c9f171f139a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597123"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= 运算符

另一个的值移**HStringReference**对象与当前**HStringReference**对象。

## <a name="syntax"></a>语法

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>参数

*other*  
将现有**HStringReference**对象。

## <a name="remarks"></a>备注

现有值*其他*对象复制到当前**HStringReference**对象，然后*其他*对象被销毁。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)