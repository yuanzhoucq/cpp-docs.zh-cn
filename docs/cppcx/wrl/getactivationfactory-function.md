---
title: GetActivationFactory 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: 82c83e95648eeb0fc8985777156659a2ffb876a8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783848"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函数

检索指定模板参数的类型的激活工厂。

## <a name="syntax"></a>语法

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>参数

*T*<br/>
模板参数，用于指定的激活工厂的类型。

*activatableClassId*<br/>
激活工厂可以生成的类的名称。

*factory*<br/>
此操作完成后，对类型的激活工厂的引用*T*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误 HRESULT，指示此操作失败的原因。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Windows::Foundation

## <a name="see-also"></a>请参阅

[Windows::Foundation 命名空间](windows-foundation-namespace.md)