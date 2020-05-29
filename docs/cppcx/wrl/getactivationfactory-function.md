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
ms.openlocfilehash: 430b4ed3f6a02fd3db2bcab05fbb7f21f5367b5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213975"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函数

检索由模板参数指定的类型的激活工厂。

## <a name="syntax"></a>语法

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>parameters

*T*<br/>
指定激活工厂类型的模板参数。

*activatableClassId*<br/>
激活工厂可以生成的类的名称。

*集*<br/>
此操作完成后，将引用对类型*T*的激活工厂。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK;否则，会出现错误 HRESULT，指示此操作失败的原因。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Windows：： Foundation

## <a name="see-also"></a>另请参阅

[Windows::Foundation 命名空间](windows-foundation-namespace.md)
