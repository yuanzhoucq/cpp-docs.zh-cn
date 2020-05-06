---
title: 对预处理器的指令
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234135"
---
# <a name="directives-to-the-preprocessor"></a>对预处理器的指令

“指令”指示 C 预处理器在编译之前先对程序的文本执行特定操作。 《预处理器参考》  中完整描述了[预处理器指令](../preprocessor/preprocessor-directives.md)。 本示例使用预处理器指令 `#define`：

```
#define MAX 100
```

该语句告知编译器在编译前将 `MAX` 的每个匹配项替换为 `100`。 C 编译器预处理器指令为：

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|#ifndef |**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)
