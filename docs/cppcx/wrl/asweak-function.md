---
title: AsWeak 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 45df6332fccb2a22284eb6478c7554d87318ca78
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021393"
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

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL 命名空间](microsoft-wrl-namespace.md)