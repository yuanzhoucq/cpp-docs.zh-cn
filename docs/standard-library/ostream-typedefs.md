---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

通过专用于 `char` 的 basic_ostream 和专用于 `char` 的 `char_traits` 创建类型。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

此类型是模板类 [basic_ostream](../standard-library/basic-ostream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。

## <a name="wostream"></a>  wostream

通过专用于 `wchar_t` 的 basic_ostream 和专用于 `wchar_t` 的 `char_traits` 创建类型。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

此类型是模板类 [basic_ostream](../standard-library/basic-ostream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。

## <a name="see-also"></a>请参阅

[\<ostream>](../standard-library/ostream.md)<br/>
