---
title: 'Hstring:: Makereference 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 061b3be0e642bb8e7406f54a469723c70559d85a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610156"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference 方法

创建`HStringReference`从指定的字符串参数的对象。

## <a name="syntax"></a>语法

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>参数

*sizeDest*  
一个模板参数，指定的目标大小`HStringReference`缓冲区。

*str*  
对宽字符串的引用。

*Len*  
最大长度*str*要在此操作中使用的参数缓冲区。 如果*len*参数未指定，整个*str*使用参数。

## <a name="return-value"></a>返回值

`HStringReference`对象，其值为与指定相同*str*参数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)