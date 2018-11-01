---
title: to_vector 函数
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: a2054e6e787dcf9137a087dd53264c7f98461d69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508948"
---
# <a name="tovector-function"></a>to_vector 函数

返回 `std::vector` ，其值与指定 IVector 或 IVectorView 参数所代表的集合相同。

## <a name="syntax"></a>语法

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型参数。

*v*<br/>
提供对基础 Vector 或 VectorView 对象访问的 IVector 或 IVectorView 接口。

### <a name="return-value"></a>返回值

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Windows::Foundation::Collections

## <a name="see-also"></a>请参阅

[Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)