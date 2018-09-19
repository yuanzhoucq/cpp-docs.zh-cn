---
title: 项目生成错误 PRJ0009 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efeb110823e801dd86a503a7069c4898f400769e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057179"
---
# <a name="project-build-error-prj0009"></a>项目生成错误 PRJ0009

生成无法打开日志，以进行写入。

**请确保文件未被另一个进程打开并且未被写保护。**

设置后**生成日志记录**属性设置为**是**和执行生成或重新生成，Visual c + + 程序无法以独占方式打开生成日志。

检查**生成日志记录**通过打开设置**选项**对话框中 (在**工具**菜单上，单击**选项**命令)，然后选择**VC + + Build**中**项目**文件夹。 生成文件为 buildlog.htm，并且会写入到中间目录 $(IntDir)。

此错误的可能原因：

- 将运行两个进程的 Visual c + + 和尝试同时生成的同一个项目在这种相同的配置。

- 在锁定文件的进程中打开生成日志文件。

- 用户没有权限创建的文件。

- 当前用户没有写访问权限的文件的 BuildLog.htm。