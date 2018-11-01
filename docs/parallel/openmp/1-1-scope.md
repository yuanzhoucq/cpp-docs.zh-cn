---
title: 1.1 范围
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449200"
---
# <a name="11-scope"></a>1.1 范围

此规范介绍仅用户指定的并行化，其中用户显式指定要执行的编译器和运行时系统以并行执行程序的操作。 OpenMP C 和 c + + 实现不需要检查依赖项、 冲突、 死锁、 争用条件或不正确的程序执行会导致其他问题。 用户负责确保应用程序使用 OpenMP C 和 c + + API 构造正确执行。 本文档未介绍编译器生成自动并行化和编译器的指令，以帮助此类并行化。