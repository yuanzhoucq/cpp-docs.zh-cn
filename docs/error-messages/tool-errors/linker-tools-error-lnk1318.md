---
title: 链接器工具错误 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160986"
---
# <a name="linker-tools-error-lnk1318"></a>链接器工具错误 LNK1318

> 意外的 PDB 错误;*会导致*'*详细信息*

链接器遇到意外的错误时打开、 读取或写入 PDB 文件。

此错误消息生成的 PDB 文件中不常见的问题。 *会导致*并*详细信息*发生失败时，链接器表示提供的信息。 这可能不是非常有用，作为处理的 PDB 文件具有单独且信息更丰富的错误消息时的常见错误。

错误的源并不常见，因为没有一般建议仅可用于解决此问题：

- 在你生成的目录中执行清理操作，然后执行完全生成你的解决方案。

- 重新启动计算机，或检查孤立或挂起 mspdbsrv.exe 进程并在任务管理器终止它们。

- 关闭在项目目录中的防病毒检查。

- 使用[/Zf](../../build/reference/zf.md)编译器选项，如果使用[/MP](../../build/reference/mp-build-with-multiple-processes.md)使用 MSBuild 或另一个并行生成过程。

- 尝试使用 64 位托管工具集生成。

- 序列化链接来根据需要缓解并行链接问题。 可能导致此错误，如果 mspdbsrv.exe 由一个实例的链接，启动和关闭的情况下进行链接的另一个实例之前使用它。 此修补程序的缺点是您项目的生成可能需要相当长的时间才能完成。