---
title: begin 函数
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258286"
---
# <a name="begin-function"></a>begin 函数

返回指向指定接口参数所访问的集合开头的迭代器。

## <a name="syntax"></a>语法

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型参数。

*v*<br/>
向量的集合\<T > 或 VectorView\<T > 对象访问的 IVector\<T > 或 IVectorView\<T > 接口。

*i*<br/>
任意对象集合的 Windows 运行时访问的 IIterable\<T > 接口。

### <a name="return-value"></a>返回值

指向集合开头的迭代器。

### <a name="remarks"></a>备注

前两个模板函数返回迭代器，第三个模板函数返回输入迭代器。

返回的对象开始的 VectorIterator 是存储类型 VectorProxy 元素的代理迭代器\<T >。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Windows::Foundation::Collections

## <a name="see-also"></a>请参阅

[Windows::Foundation::Collections 命名空间](../cppcx/windows-foundation-collections-namespace-c-cx.md)
