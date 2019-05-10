---
title: Tasks.vs.json 架构引用 (C++)
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315048"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json (C++)

可向“打开文件夹”项目添加 `tasks.vs.json` 文件来定义任意任务，然后从“解决方案资源管理器”上下文菜单中调用它。 CMake 项目通常不使用此文件，因为所有生成命令都在 `CMakeLists.txt` 中指定。 非 CMake 生成系统可在此处指定生成命令和调用生成脚本。 有关使用 tasks.vs.json 的常规信息，请参阅[为“打开文件夹”开发自定义生成和调试任务](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

