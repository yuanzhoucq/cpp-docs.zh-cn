---
title: 自定义 C++ 命令行处理 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setenvp
- _setargv
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e847cff10c7e17185f76b5e790beda3745732312
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406684"
---
# <a name="customizing-c-command-line-processing"></a>自定义 C++ 命令行处理
## <a name="microsoft-specific"></a>Microsoft 专用  
 如果程序不采用命令行自变量，则可以通过取消使用执行命令行处理的库例程来节省少量空间。 此例程称为`_setargv`和中所述[通配符扩展](../cpp/wildcard-expansion.md)。 若要禁止使用，定义中包含的文件不起作用的例程`main`函数，并将其命名`_setargv`。 在调用`_setargv`然后满足您的定义的`_setargv`，并且不会加载库版本。  
  
 同样，如果永远不会访问环境表通过`envp`参数，你可以提供你自己的空例程来代替使用`_setenvp`，环境处理例程。 正如使用`_setargv`函数，`_setenvp`必须声明为**extern"C"**。  
  
 您的程序可能会使对调用`spawn`或`exec`系列中的 C 运行时库例程。 如果是这样，则不应取消环境处理例程，因为可使用此例程将环境从父进程传递到子进程中。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)