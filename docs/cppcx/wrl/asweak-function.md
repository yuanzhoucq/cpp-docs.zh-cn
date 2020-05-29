---
title: AsWeak 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214170"
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

### <a name="parameters"></a>parameters

*T*<br/>
指向参数*p*的类型的指针。

*p*<br/>
类型的实例。

*pWeak*<br/>
此操作完成后，指向参数*p*的弱引用的指针。

## <a name="return-value"></a>返回值

S_OK，如果此操作成功，则为;否则，会出现指示失败原因的错误 HRESULT。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
