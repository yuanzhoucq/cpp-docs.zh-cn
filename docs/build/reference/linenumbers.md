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
ms.openlocfilehash: aec21026ded821f9a87e7c0c2aeefd13a927a401
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417302"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>备注

此选项显示 COFF 行号。 在对象文件中存在的行数，如果它使用编译的程序数据库 (/Zi) C7 兼容 (/ Z7)，或仅限行号 (/Zd)。 可执行文件或 DLL 包含 COFF 行号，如果它与生成调试信息链接 (/debug)。

仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)
