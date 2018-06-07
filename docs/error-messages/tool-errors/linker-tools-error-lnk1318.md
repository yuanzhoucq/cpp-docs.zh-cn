---
title: 链接器工具错误 LNK1318 |Microsoft 文档
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570681"
---
# <a name="linker-tools-error-lnk1318"></a>链接器工具错误 LNK1318

> 意外的 PDB 错误;*导致**详细信息*

链接器遇到意外的错误时打开、 读取或写入 PDB 文件。

PDB 文件中的常见问题的情况下，会产生此错误消息。 *导致*和*详细信息*出现错误时，到链接器表示可用的信息。 这可能不是非常有用，为常见的错误时应对 PDB 文件具有单独的、 更有意义的错误消息。

因为错误的来源是不常见，没有泛型建议仅可用于解决此问题：

- 在你生成的目录中执行的清理操作，然后执行完全生成你的解决方案。

- 重新启动计算机，或检查孤立或挂起 mspdbsrv.exe 进程并终止它们 TaskManager 中。

- 请关闭项目目录中的防病毒检查。

- 使用[/Zf](../../build/reference/zf.md)编译器选项，如果使用[/MP](../../build/reference/mp-build-with-multiple-processes.md)使用 MSBuild 或另一个并行生成过程。

- 通过使用 64 位托管工具集试用构建。

- 序列化链接来缓解并行链接问题，如果需要。 如果 mspdbsrv.exe 由一个实例的链接，启动和关闭的情况下完成的链接的另一个实例之前，可能导致此错误使用它。 此修补程序的缺点是你的项目生成可能需要相当长的时间才能完成。