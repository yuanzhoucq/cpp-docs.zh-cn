---
title: 'Hstring:: Operator = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9294650db7a1b18c2542603988952a80b3f1905d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598540"
---
# <a name="hstringoperator-operator"></a>HString::Operator= 运算符

另一个的值移**HString**对象与当前**HString**对象。

## <a name="syntax"></a>语法

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>参数

*other*  
将现有**HString**对象。

## <a name="remarks"></a>备注

现有值*其他*对象复制到当前**HString**对象，然后*其他*对象被销毁。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)