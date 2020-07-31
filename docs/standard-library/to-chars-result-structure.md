---
title: to_chars_result 结构
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: a840b8d030f0ed0d2a4afcc57e1bef1161c76ff3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212056"
---
# <a name="to_chars_result-struct"></a>to_chars_result 结构

## <a name="syntax"></a>语法

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>成员

|成员|描述|
|--|--|
|`ptr`| 如果 `ec` 等于，则 `errc{}` 转换成功并且 `ptr` 是写入字符的一-后端指针。 否则，将 `ptr` 具有参数的值 `to_chars()` `last` ，并且 \[ 不指定范围的第一个、最后一个的内容。|
|`ec` | 转换错误代码。 有关特定的错误代码，请参阅 [`errc`](system-error-enums.md#errc) 。|

## <a name="requirements"></a>要求

**标头：**\<charconv>

**命名空间:** std

**编译器选项：** /std： c + + 17 或更高版本是必需的

## <a name="see-also"></a>另请参阅

[to_chars](charconv-functions.md#to_chars)