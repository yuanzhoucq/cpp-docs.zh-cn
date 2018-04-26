---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 8c451b16a581ab13f87c7bcca793efe3a0f07bf5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
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
