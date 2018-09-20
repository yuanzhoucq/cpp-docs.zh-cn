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
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422644"
---
# <a name="hstringoperator-operator"></a>HString::Operator= 运算符

另一个的值移**HString**对象与当前**HString**对象。

## <a name="syntax"></a>语法

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>参数

*other*<br/>
将现有**HString**对象。

## <a name="remarks"></a>备注

现有值*其他*对象复制到当前**HString**对象，然后*其他*对象被销毁。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)