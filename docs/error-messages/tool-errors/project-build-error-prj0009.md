---
title: 项目生成错误 PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359496"
---
# <a name="project-build-error-prj0009"></a>项目生成错误 PRJ0009

生成无法打开日志，以进行写入。

**请确保文件未被另一个进程打开并且未被写保护。**

设置后**生成日志记录**属性设置为**是**执行生成或重新生成，视觉对象和C++无法以独占方式打开生成日志。

检查**生成日志记录**通过打开设置**选项**对话框中 (在**工具**菜单上，单击**选项**命令)，然后选择**VC + + Build**中**项目**文件夹。 生成文件为 buildlog.htm，并且会写入到中间目录 $(IntDir)。

此错误的可能原因：

- 运行视觉对象的两个进程C++和尝试同时生成的同一个项目在这种相同的配置。

- 在锁定文件的进程中打开生成日志文件。

- 用户没有权限创建的文件。

- 当前用户没有写访问权限的文件的 BuildLog.htm。