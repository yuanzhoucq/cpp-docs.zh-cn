---
title: 编译器警告（等级1） C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175841"
---
# <a name="compiler-warning-level-1-c4274"></a>编译器警告（等级1） C4274

已忽略 \#ident;请参阅 #pragma 注释的文档（exestr，' string '）

将用户指定的字符串插入对象或可执行文件中的 `#ident` 指令已弃用。 因此，编译器将忽略指令。

> [!CAUTION]
>  警告 C4274 建议使用[#pragma 注释（exestr，' string '）](../../preprocessor/comment-c-cpp.md)指令。 但是，此建议已弃用，并将在编译器的未来版本中进行修改。 如果使用 `#pragma` 指令，则链接器工具（LNK4229）将忽略指令生成的注释记录，并[发出警告。](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md) 建议你在应用程序中使用文件版本资源字符串，而不是 `#ident` 指令。

## <a name="to-correct-this-error"></a>更正此错误

- 删除 `#ident "`*字符串*`"` 指令。

## <a name="see-also"></a>另请参阅

[注释 (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[链接器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[使用资源文件](../../windows/working-with-resource-files.md)
