---
title: 'Hstring:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da0e8e241aeb3f0eb5096d64cd63425ca2102fb0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211166"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo 方法

复制当前**HString**到 HSTRING 对象的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>参数

*str*  
接收副本的 HSTRING。

## <a name="remarks"></a>备注

此方法调用[WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx)函数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)