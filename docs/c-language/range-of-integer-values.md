---
title: 整数值的范围 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d940824e6bb1dc728cb999c1e820cb7adcedf8ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092643"
---
# <a name="range-of-integer-values"></a>整数值的范围

**ANSI 3.1.2.5**：各种类型的整数值的表示形式和集

整数包含 32 位（4 个字节）。 带符号整数以 2 的补数的形式表示。 最高有效位保存符号：1 表示负数，0 表示整数或零。 下面列出了这些值：

|类型|最小值和最大值|
|----------|-------------------------|
|**unsigned short**|0 到 65535|
|`signed short`|-32768 到 32767|
|`unsigned long`|0 到 4294967295|
|**signed long**|-2147483648 到 2147483647|

## <a name="see-also"></a>请参阅

[整数](../c-language/integers.md)