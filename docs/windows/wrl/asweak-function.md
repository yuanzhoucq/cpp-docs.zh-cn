---
title: AsWeak 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 1332aa140a8298590ad83158e0ec1b75035c4e92
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335908"
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

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)