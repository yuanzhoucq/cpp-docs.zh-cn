---
title: ActivateInstance 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 4525ee74bc63a9655e7f1142fb1b2b6812d82bb6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784058"
---
# <a name="activateinstance-function"></a>ActivateInstance 函数

注册并检索实例的指定类型定义中指定的类 id。

## <a name="syntax"></a>语法

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>参数

*T*<br/>
要激活的类型。

*activatableClassId*<br/>
定义参数的类 ID 的名称*T*。

*instance*<br/>
此操作完成后，对的实例的引用*T*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误 HRESULT，指示错误的原因。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Windows::Foundation

## <a name="see-also"></a>请参阅

[Windows::Foundation 命名空间](windows-foundation-namespace.md)