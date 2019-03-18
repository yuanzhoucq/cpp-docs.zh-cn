---
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: ea4c3ac2ad582e0fe364f2da26511a66e9dc376c
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57811948"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>备注

此选项显示 COFF 行号。 在对象文件中存在的行数，如果它使用编译的程序数据库 (/Zi) C7 兼容 (/ Z7)，或仅限行号 (/Zd)。 可执行文件或 DLL 包含 COFF 行号，如果它与生成调试信息链接 (/debug)。

仅[/HEADERS](headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
