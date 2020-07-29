---
title: setlocale 杂注
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 9603c132610e0cfb1e8f955be48271870527105b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219373"
---
# <a name="setlocale-pragma"></a>setlocale 杂注

定义在转换宽字符常量和字符串文本时要使用的*区域设置*、国家/地区和语言。

## <a name="syntax"></a>语法

> **#pragma setlocale （"** [ *locale 字符串*] **"）**

## <a name="remarks"></a>备注

由于将多字节字符转换为宽字符的算法可能会因区域设置而异，或编译可能发生在不同的区域设置中，可执行文件将在此区域设置中运行，此杂注提供了在编译时指定目标区域设置的方法。 它可确保以正确的格式存储宽字符字符串。

默认*区域设置*是 ""。

"C" 区域设置将字符串中的每个字符映射为其值 **`wchar_t`** 。 的其他有效值 `setlocale` 是在[语言字符串](../c-runtime-library/language-strings.md)列表中找到的条目。 例如，可以指定：

```cpp
#pragma setlocale("dutch")
```

指定语言字符串的能力取决于计算机上的代码页和语言 ID 支持。

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
