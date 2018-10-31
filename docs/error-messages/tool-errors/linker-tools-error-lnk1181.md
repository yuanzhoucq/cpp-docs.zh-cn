---
title: 链接器工具错误 LNK1181 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 787c6c35b698b5dce57c4aaf3acb4eca496ead95
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072156"
---
# <a name="linker-tools-error-lnk1181"></a>链接器工具错误 LNK1181

无法打开输入的文件 filename

找不到链接器`filename`因为它不存在或找不到路径。

错误 lnk1181 一些常见原因：

- `filename` 附加依赖项上链接器行中，但该文件不存在，因此引用。

- 一个 **/LIBPATH**语句，用于指定目录包含`filename`缺少。

若要解决上述问题，请确保链接器行上引用的任何文件都存在于系统。  此外请确保没有 **/LIBPATH**语句为每个目录，其中包含依赖于链接器的文件。

有关详细信息，请参阅[用作链接器输入的.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。

Lnk1181 另一个可能的原因是没有具有嵌入的空格的长文件名括在引号中。  在这种情况下，链接器将仅识别第一个空格，文件名，然后假定的文件的扩展名。 目标这种情况下的解决方案是将括起来的长文件名 （路径和文件名） 引起来。

使用编译[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项可能导致 LNK1181，因为该选项将取消创建的.obj 文件。

## <a name="see-also"></a>请参阅

[/LIBPATH（附加的 Libpath）](../../build/reference/libpath-additional-libpath.md)