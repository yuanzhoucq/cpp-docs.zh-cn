---
title: operator&lt; 运算符（Microsoft：： WRL）
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 04f5598667f7e0e036f0a55cd3f9cc52b5356299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213637"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operator&lt; 运算符（Microsoft：： WRL）

确定一个对象的地址是否小于另一个对象的地址。

## <a name="syntax"></a>语法

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>parameters

*a*<br/>
左对象。

*b*<br/>
右对象。

## <a name="return-value"></a>返回值

如果*的地址*小于*b*的地址，**则为 true** ;否则**为 false**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
