---
title: operator!= 运算符 (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator!=
ms.assetid: 785435da-87a6-4454-9bce-9d288a96dc26
ms.openlocfilehash: 6068a7ddad78e3347f6987b30cc2884dc3f648fd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040078"
---
# <a name="operator-operator-microsoftwrl"></a>operator!= 运算符 (Microsoft::WRL)

不等运算符[ComPtr](comptr-class.md)并[ComPtrRef](comptrref-class.md)对象。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>参数

*a*<br/>
左对象。

*b*<br/>
右对象。

## <a name="return-value"></a>返回值

**true**如果对象不相等; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL 命名空间](microsoft-wrl-namespace.md)