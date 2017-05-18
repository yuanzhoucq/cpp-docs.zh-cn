---
title: "部署、运行和调试 Linux 项目 | Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: db868094a8f10ad05ed6f95bf8a4c8a29a2c941e
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---

# <a name="deploy-run-and-debug-your-project"></a>部署、运行和调试项目

项目现已创建，你需要连接到 Linux 计算机，这是编译、执行和调试代码的地方。

1. 使用 Visual Studio 中的标准下拉列表设置远程目标体系结构，如图所示：![远程体系结构](media/architecture.png)

与 Linux 项目交互并对其进行调试方法有若干种。

* 传统的 Visual Studio 功能（例如断点、监视窗口和悬停在变量上方）都将如常工作，因此，你可以像平时一样进行调试。
* 使用“**调试 > Linux 控制台**”菜单项可打开特殊的 Linux 控制台窗口。

  ![Linux 控制台菜单](media/consolemenu.png)

  此控制台将显示来自目标计算机的全部控制台输出并接收输入，然后将其发送到目标计算机。

  ![Linux 控制台窗口](media/consolewindow.png)

* 可以使用项目“**调试**”属性页中的“**程序参数**”项将命令行参数传递给可执行文件。
  
  ![程序参数](media/settings_programarguments.png)

* GDB 用于调试在 Linux 上运行的应用程序。  但是，能以两种不同的模式运行，可从项目“**调试**”属性页中的“**调试模式**”选项中进行选择：

  ![GDB 选项](media/settings_debugger.png)

  | 选择 | 说明
  | --------- | ---
  | gdbserver | GDB 在本地运行，连接到运行在远程系统上的 gdbserver。  请注意，这是 Linux 控制台窗口唯一支持的模式。 
  | gdb       | Visual Studio 调试器驱动远程系统上的 GDB，如果 GDB 的本地版本与目标计算机上安装的版本不兼容，则远程系统上的 GDB 更易兼容

* 可使用“**其他调试程序命令**”条目将特定调试程序选项传递到 GDB。  例如，你可能需要忽略 SIGILL（非法指令）信号。  那么，可以使用“**句柄**”命令来实现此目的，方法是：  将以下命令添加到如上图中所示的“**其他调试程序命令**”条目：

  ```handle SIGILL nostop noprint```

