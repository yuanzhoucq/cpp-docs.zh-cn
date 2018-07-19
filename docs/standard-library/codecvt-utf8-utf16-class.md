---
title: codecvt_utf8_utf16 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 545fda08a027b1610f82d17c89ae98241ee5502b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958125"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

表示在编码为 UTF-16 的宽字符和编码为 UTF-8 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

*Elem*宽字符元素类型。
*Maxcode*的最大的区域设置 facet 的字符数。
*模式*的区域设置 facet 的配置信息。

## <a name="remarks"></a>备注

字节流可以写入二进制文件或文本文件。

## <a name="requirements"></a>要求

标头：<codecvt> Namespace: std
