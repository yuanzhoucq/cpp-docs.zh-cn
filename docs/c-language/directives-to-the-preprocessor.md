---
title: 对预处理器的指令 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1ddecf1e205cc9a6d7f09a27fbf243417540e49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033558"
---
# <a name="directives-to-the-preprocessor"></a>对预处理器的指令

“指令”指示 C 预处理器在编译之前先对程序的文本执行特定操作。 《预处理器参考》中完整描述了[预处理器指令](../preprocessor/preprocessor-directives.md)。 本示例使用预处理器指令 `#define`：

```
#define MAX 100
```

该语句告知编译器在编译前将 `MAX` 的每个匹配项替换为 `100`。 C 编译器预处理器指令为：

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|#ifndef|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)