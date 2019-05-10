---
title: 命令行错误 D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214176"
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