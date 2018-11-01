---
title: 错误 C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 3fb4db30d91e0dd8c9dbeeebca46210122e5ff07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663146"
---
# <a name="fatal-error-c1905"></a>错误 C1905

前端和后端不兼容（必须面向同一处理器）

.Obj 文件生成的编译器前端 (C1.dll) 该目标的一个处理器，如 x86、 ARM、 或 x64，但以不同处理器为目标的后端 (C2.dll) 读取，会出现此错误。

若要解决此问题，请确保你使用的前端和后端相匹配。 对于 Visual Studio 中创建的项目，这是默认的。 如果已编辑该项目文件并使用通向编译器工具的不同路径，则可能会出现此错误。 如果未特别设置编译器工具的路径，则你的 Visual Studio 安装损坏时可能发生此错误。 例如，你可能已将编译器 .dll 文件从一个位置复制到另一个位置。 使用**程序和功能**Windows 控制面板来修复或重新安装 Visual Studio 中。