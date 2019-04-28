---
title: 链接器工具错误 LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299005"
---
# <a name="linker-tools-error-lnk2027"></a>链接器工具错误 LNK2027

无法解析的模块引用 module

传递给链接的文件都不使用指定的模块上具有依赖项 **/ASSEMBLYMODULE**也不会直接向链接器传递。

若要解决 LNK2027，请执行以下操作：

- 不要传递给链接器具有模块依赖项的文件。

- 指定的模块 **/ASSEMBLYMODULE**。

- 如果该模块是安全的 .netmodule，则将它直接传递给链接器。

有关详细信息，请参阅[/ASSEMBLYMODULE （添加对程序集 MSIL 模块）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)并[用作链接器输入的.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。