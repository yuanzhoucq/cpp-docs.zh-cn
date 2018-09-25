---
title: 'Hstringreference:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61474e3891def73114f8efc101e1132d5d2593b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402728"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo 方法

复制当前**HStringReference**到 HSTRING 对象的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*str*<br/>
接收副本的 HSTRING。

## <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx)函数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)