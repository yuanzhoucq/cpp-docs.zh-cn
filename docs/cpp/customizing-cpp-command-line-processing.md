---
title: 自定义 C++ 命令行处理
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857549"
---
# <a name="customizing-c-command-line-processing"></a>自定义 C++ 命令行处理

**Microsoft 专用**

如果程序不采用命令行自变量，则可以通过取消使用执行命令行处理的库例程来节省少量空间。 此例程 `_setargv` 调用，并在[通配符扩展](../cpp/wildcard-expansion.md)中进行了介绍。 若要禁止使用，请在包含 `main` 函数的文件中定义不执行任何操作的例程，并将其命名为 `_setargv`。 然后，`_setargv`的定义满足对 `_setargv` 的调用，且未加载库版本。

同样，如果永远不会通过 `envp` 参数访问环境表，则可以提供自己的空例程用于替代 `_setenvp`（环境处理例程）。 与 `_setargv` 函数一样，`_setenvp` 必须声明为**extern "C"** 。

程序可能会调用 C 运行库中的 `spawn` 或 `exec` 的例程系列。 如果是这样，则不应取消环境处理例程，因为可使用此例程将环境从父进程传递到子进程中。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[main：程序启动](../cpp/main-program-startup.md)