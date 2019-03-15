---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: a0456fd9ed1729b4a6cfa200a54ba211a64e94ea
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813274"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>备注

此选项显示在库中定义的公共符号。 指定要显示在对象的顺序，以及它们的偏移量的符号的 1 参数。 指定要显示的偏移量和对象的索引号的 2 个自变量，然后列出按字母顺序，以及每个对象索引的符号。 若要获取这两个输出，请指定不带该数字参数 /LINKERMEMBER。

仅[/HEADERS](headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
