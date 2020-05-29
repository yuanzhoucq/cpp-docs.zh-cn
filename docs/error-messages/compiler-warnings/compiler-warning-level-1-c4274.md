---
title: 编译器警告（级别 1） C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377078"
---
# <a name="compiler-warning-level-1-c4274"></a>编译器警告（级别 1） C4274

\#标识被忽略;请参阅文档，了解#pragma注释（exestr，"字符串"）

该`#ident`指令在对象或可执行文件中插入用户指定的字符串，该指令将被弃用。 因此，编译器忽略该指令。

> [!CAUTION]
> 警告 C4274 建议您使用[#pragma注释（exestr，"字符串"）](../../preprocessor/comment-c-cpp.md)指令。 但是，此建议被弃用，并将在编译器的未来版本中进行修订。 如果使用该`#pragma`指令，链接器工具 （LINK.exe） 将忽略该指令生成的注释记录，并发出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 我们建议您在应用程序中`#ident`使用文件版本资源字符串，而不是该指令。

## <a name="to-correct-this-error"></a>更正此错误

- 删除`#ident "`*字符串*`"`指令。

## <a name="see-also"></a>另请参阅

[注释 (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[链接器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[使用资源文件](../../windows/working-with-resource-files.md)
