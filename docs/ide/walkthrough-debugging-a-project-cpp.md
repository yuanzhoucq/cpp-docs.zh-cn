---
title: "演练： 调试项目 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c9789a7deafacf09ad615f416a446da4eba8150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-debugging-a-project-c"></a>演练：调试项目 (C++)
在本演练中，你将修改程序以修复在测试项目时发现的问题。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成中列出的更早版本相关的演练[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>若要修复有 bug 的程序  
  
1.  若要查看销毁 `Cardgame` 对象时发生的情况，请查看 `Cardgame` 类的析构函数。  
  
     在菜单栏上，选择**视图**，**类视图**。  
  
     在**类视图**窗口中，展开**游戏**项目树并选择**Cardgame**类来显示类成员和方法。  
  
     打开的快捷菜单**~Cardgame(void)**析构函数，然后选择**转到定义**。  
  
2.  若要在 Cardgame 终止时减少 `totalParticipants`，请在 `Cardgame::~Cardgame` 析构函数的左大括号和右大括号之间键入以下代码。  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  在更改后，Cardgame.cpp 文件应类似如下：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
5.  在生成完成，以运行它在调试模式下通过选择**调试**，**启动调试**在菜单栏上，或通过选择 F5 键。 在第一个断点处暂停程序。  
  
6.  若要逐步执行程序，请在菜单栏上，选择**调试**，**逐过程**，或选择 F10 键。  
  
     请注意，执行每个 Cardgame 构造函数后，`totalParticipants` 的值会增大。 在 `PlayGames` 函数返回时，由于每个 Cardgame 实例都超出范围且被删除（并且调用析构函数），因此 `totalParticipants` 会减小。 之前`return`执行语句，`totalParticipants`等于 0。  
  
7.  继续逐步执行程序直到其退出，或将其通过选择运行**调试**，**运行**在菜单栏上，或通过选择 F5 键。  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：** [演练： 测试项目 （c + +）](../ide/walkthrough-testing-a-project-cpp.md) &#124;**下一步：**[演练： 部署程序 （c + +）](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)