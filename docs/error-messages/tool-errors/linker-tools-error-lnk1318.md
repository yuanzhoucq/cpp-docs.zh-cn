---
title: 链接器工具错误 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: cce2c03783039a62b5cb6f60ecf8d76b23589483
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446696"
---
# <a name="linker-tools-error-lnk1318"></a>链接器工具错误 LNK1318

> 意外的 PDB 错误;*原因*"*详细信息*"

链接器在打开、读取或写入 PDB 文件时遇到意外错误。

对于 PDB 文件中的罕见问题，将生成此错误消息。 *原因*和*详细信息*表示当发生故障时链接器可用的信息。 这可能并不是很有用，因为在处理 PDB 文件时出现常见错误，它们具有不同的、更丰富的错误消息。

由于错误的根源并不常见，因此仅有可用于解决此问题的通用建议：

- 在生成目录中执行清理操作，然后执行解决方案的完整生成。

- 重新启动计算机，或者在 TaskManager 中检查是否有被或无 mspdbsrv.exe 响应的进程。

- 关闭项目目录中的防病毒检查。

- 如果将[/mp](../../build/reference/mp-build-with-multiple-processes.md)用于 MSBuild 或其他并行生成过程，请使用[/Zf](../../build/reference/zf.md)编译器选项。

- 尝试使用64位托管工具集生成。

- 序列化链接以根据需要缓解并行链接问题。 如果 mspdbsrv.exe 由一个链接实例启动，则可能会导致此错误，并在使用它的另一个链接实例完成之前关闭。 此修补程序的缺点是您的项目生成可能需要更长的时间才能完成。
