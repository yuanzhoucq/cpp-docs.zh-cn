---
title: 宏内的特殊字符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a94001e2f912049518120911c25ae64afa24da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721409"
---
# <a name="special-characters-in-macros"></a>宏内的特殊字符

定义指定了注释后，数字符号 （#）。 若要在宏中指定文本的数字符号，请使用脱字号 (^)，如 ^ #。

美元符号 （$） 指定宏调用。 若要指定文本 $，请使用 $$。

若要扩展到新行的定义，以结束行反斜杠 (\\)。 调用该宏时，反斜杠和换行符字符替换空格。 若要指定在行末尾的文本反斜杠，前面插入符号 (^)，加上或其后加上注释说明符 (）。

若要指定文本换行字符，如结束的脱字号 (^)，行：

```
CMDS = cls^
dir
```

## <a name="see-also"></a>请参阅

[定义 NMAKE 宏](../build/defining-an-nmake-macro.md)