---
title: "自定义 c + + 命令行处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 977ab6f5a7a8dbddf045e83a14127ac979a114a9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="customizing-c-command-line-processing"></a>自定义 C++ 命令行处理
## <a name="microsoft-specific"></a>Microsoft 专用  
 如果程序不采用命令行自变量，则可以通过取消使用执行命令行处理的库例程来节省少量空间。 此例程称为**_setargv**和中所述[通配符扩展](../cpp/wildcard-expansion.md)。 若要禁止使用它，请定义不执行任何操作中包含的文件的例程**主要**函数，并将其命名**_setargv**。 调用**_setargv**然后按照你定义满足**_setargv**，并且不加载库版本。  
  
 同样，如果你永远不会访问环境表通过`envp`自变量，你可以提供你自己的空例程用于代替了**_setenvp**，环境处理例程。 正如使用**_setargv**函数， **_setenvp**必须声明为**extern"C"**。  
  
 程序可以调用**spawn**或`exec`系列 C 运行时库中的例程。 如果是这样，则不应取消环境处理例程，因为可使用此例程将环境从父进程传递到子进程中。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [main：程序启动](../cpp/main-program-startup.md)
