---
title: codecvt_utf8 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dce174d9c6edca45946ba8ad60165e62e3591fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718479"
---
# <a name="codecvtutf8"></a>codecvt_utf8

表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-8 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

*Elem*<br/>
宽字符元素类型。

*Maxcode*<br/>
区域设置 facet 的最大字符数。

*模式*<br/>
配置区域设置 facet 的信息。

## <a name="remarks"></a>备注

字节流可以写入二进制文件或文本文件。

## <a name="requirements"></a>要求

标头： \<codecvt > \

Namespace: std
