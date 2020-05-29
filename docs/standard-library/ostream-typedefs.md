---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373583"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

从basic_ostream创建一个类型，该类型专门用于**字符**，并且`char_traits`专门用于**字符**。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="wostream"></a><a name="wostream"></a>沃溪

从专门用于**wchar_t**和`char_traits`专门wchar_t的basic_ostream创建**类型。**

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专门用于具有默认字符特征的类型**wchar_t**元素。

## <a name="see-also"></a>另请参阅

[\<流>](../standard-library/ostream.md)
