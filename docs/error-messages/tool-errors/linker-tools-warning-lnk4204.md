---
title: 链接器工具警告 LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475138"
---
# <a name="linker-tools-warning-lnk4204"></a>链接器工具警告 LNK4204

filename 缺少引用模块中; 调试信息正在链接对象，如同没有调试信息一样

.Pdb 文件的错误签名。 链接器将继续链接没有调试信息的对象。 你可能想要重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项。

如果某些库中的对象引用不再存在的文件，会发生 LNK4204。 发生此情况时重新生成解决方案，例如：可能会删除并不会重新生成由于编译错误的对象文件。 在这种情况下，可以使用编译 **/z7**，或 **/Fd**，以更新对象来引用单个文件每个库 （不是默认.pdb 文件名称）。  有关详细信息，请参阅 [/Fd（程序数据库文件名）](../../build/reference/fd-program-database-file-name.md)。  请确保每次更新源代码管理系统中，与以下库保存.pdb。