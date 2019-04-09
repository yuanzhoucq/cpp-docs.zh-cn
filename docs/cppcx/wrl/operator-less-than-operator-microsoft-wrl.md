---
title: '运算符&lt;运算符 (microsoft:: wrl)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 4887a7ebf3906edbc4a5a2a723caff0ad7732c46
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036846"
---
# <a name="operatorlt-operator-microsoftwrl"></a>运算符&lt;运算符 (microsoft:: wrl)

确定一个对象的地址是否小于另一个。

## <a name="syntax"></a>语法

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>参数

*a*<br/>
左对象。

*b*<br/>
右对象。

## <a name="return-value"></a>返回值

**true**如果的地址的地址少于*b*; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL 命名空间](microsoft-wrl-namespace.md)