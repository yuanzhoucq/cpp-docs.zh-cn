---
title: AsWeak 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dfd626a3e0ca1866f6db046554220c6e631c18b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394304"
---
# <a name="asweak-function"></a>AsWeak 函数

检索对指定实例的弱引用。

## <a name="syntax"></a>语法

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>参数

*T*<br/>
指向参数的类型的指针*p*。

*p*<br/>
类型的实例。

*pWeak*<br/>
此操作完成后，对参数的弱引用的指针*p*。

## <a name="return-value"></a>返回值

如果成功，则此操作，则为 S_OK否则为错误 HRESULT，指示失败的原因。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)