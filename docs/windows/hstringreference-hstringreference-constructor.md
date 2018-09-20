---
title: 'Hstringreference:: Hstringreference 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6123f87abb9922a9736ac56f64d28e78887a0fdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403563"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference 构造函数

初始化的新实例**HStringReference**类。

## <a name="syntax"></a>语法

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>参数

*sizeDest*<br/>
指定的目标大小的模板参数**HStringReference**缓冲区。

*str*<br/>
对宽字符串的引用。

*Len*<br/>
最大长度*str*要在此操作中使用的参数缓冲区。 如果*len*参数未指定，整个*str*使用参数。 如果*len*大于*sizeDest*， *len*设置为*sizeDest*-1。

*other*<br/>
另一个**HStringReference**对象。

## <a name="remarks"></a>备注

第一个构造函数初始化新**HStringReference**相同大小与参数的对象*str*。

第二个构造函数初始化新**HStringReference**对象的大小指定由参数*len*。

第三个构造函数初始化新**HStringReference**对象的值*其他*参数，然后再销毁*其他*参数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HStringReference 类](../windows/hstringreference-class.md)