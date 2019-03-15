---
title: Tasks.vs.json 架构参考 （c + +）
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824484"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json （c + +）

一个`tasks.vs.json`文件可以添加到打开文件夹项目来定义任何任意任务，然后调用其从**解决方案资源管理器**上下文菜单。 CMake 项目通常不使用此文件中指定生成的所有命令因为`CMakeLists.txt`。 对于非 CMake 生成系统，这是可以在此指定生成命令，并调用生成脚本。 有关使用 tasks.vs.json 的常规信息，请参阅[自定义生成和调试的"打开文件夹"开发任务](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

