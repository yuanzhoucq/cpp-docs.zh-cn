---
title: 命令行错误 D8027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8234835d3bb0545c8a72bf35cfb55b2e18bc7da2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070374"
---
# <a name="command-line-error-d8027"></a>命令行错误 D8027

无法执行组件

编译器无法运行给定的编译器组件或链接器。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 内存不足，无法加载该组件。 当 NMAKE 调用的编译器，外部生成文件运行编译器。

1. 当前操作系统无法运行该组件。 请确保路径点的可执行文件适合于您的操作系统。

1. 该组件已损坏。 将从分发的磁盘，使用安装程序组件重新复制。

1. 未正确指定了一个选项。 例如：

    ```
    cl /B1 file1.c
    ```