---
title: 宏内的特殊字符
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: aac7b07500d2a129194e7234210a590cb5d0f19a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824530"
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

[定义 NMAKE 宏](defining-an-nmake-macro.md)
