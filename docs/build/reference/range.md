---
title: -范围 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e7525b8c1872616182141d624bff8f94571952
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712187"
---
# <a name="range"></a>/RANGE

修改 dumpbin 与其他 dumpbin 选项，例如 /RAWDATA 或 /DISASM 一起使用时的输出。

## <a name="syntax"></a>语法

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>参数

*vaMin*<br/>
要 dumpbin 操作以开始虚拟地址。

*vaMax*<br/>
（可选）想要结束的 dumpbin 操作虚拟地址。 如果未指定，dumpbin 将转到文件末尾。

## <a name="remarks"></a>备注

若要查看映像的虚拟地址，请使用映射文件 （RVA + Base） 的映像 **/DISASM**或 **/HEADERS** dumpbin 或在 Visual Studio 调试器中的反汇编窗口的选项。

## <a name="example"></a>示例

在此示例中， **/范围**用于修改的显示 **/disasm**选项。 在此示例中，以十进制数表示的起始值和结束值指定为十六进制数。

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](../../build/reference/dumpbin-options.md)