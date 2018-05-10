---
title: 1.1 确定范围 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="11-scope"></a>1.1 范围
此规范涵盖仅用户定向的并行化，其中用户显式指定要执行的编译器和运行时系统以便并行执行程序的操作。 检查依赖关系、 冲突、 死锁、 争用条件或其他问题，从而导致不正确的程序执行时，不需执行 OpenMP C 和 c + + 实现。 用户负责确保应用程序使用 OpenMP C 和 c + + API 构造正确执行。 本文档不涉及编译器生成自动并行化和到编译器的指令，以协助此类并行化。