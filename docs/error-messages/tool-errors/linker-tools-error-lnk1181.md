---
title: 链接器工具错误 LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195248"
---
# <a name="linker-tools-error-lnk1181"></a>链接器工具错误 LNK1181

无法打开输入文件 "filename"

链接器找不到 `filename`，因为它不存在或找不到该路径。

错误 LNK1181 的一些常见原因包括：

- `filename` 作为链接行的附加依赖项进行引用，但该文件不存在。

- 一个 **/LIBPATH**语句，该语句指定包含 `filename` 的目录。

若要解决上述问题，请确保在链接器行上引用的任何文件都存在于系统上。  此外，请确保每个包含链接器相关文件的目录都有 **/LIBPATH**语句。

有关详细信息，请参阅[用作链接器输入的 .Lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。

导致 LNK1181 的另一个可能原因是，带有嵌入空格的长文件名没有用引号引起来。  在这种情况下，链接器将仅识别最大为第一个空格的文件名，然后假定文件扩展名为 .obj。 这种情况的解决方法是将长文件名（路径加上文件名）括在引号中。

使用[/p （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项进行编译会导致 LNK1181，因为该选项会禁止创建 .obj 文件。

## <a name="see-also"></a>另请参阅

[/LIBPATH（附加的 Libpath）](../../build/reference/libpath-additional-libpath.md)
