---
title: back_inserter 函数
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750736"
---
# <a name="backinserter-function"></a>back_inserter 函数

返回用于在指定集合末尾插入元素的迭代器。

## <a name="syntax"></a>语法

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>参数

*T*<br/>
模板类型参数。

*v*<br/>
提供对基础集合访问的接口指针。

### <a name="return-value"></a>返回值

迭代器。

### <a name="requirements"></a>要求

**标头：** collection.h

**命名空间：** Windows::Foundation::Collections

## <a name="see-also"></a>请参阅

[Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)
