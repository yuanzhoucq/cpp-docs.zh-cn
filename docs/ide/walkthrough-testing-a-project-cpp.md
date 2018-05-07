---
title: 演练： 测试项目 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9455fa9bf3c9f903f5018a1263978913aa35b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-testing-a-project-c"></a>演练：测试项目 (C++)
在调试模式下运行程序时，可以使用断点来暂停程序，以检查变量和对象的状态。  
  
 在本演练中，你将监视其值的变量，在程序运行并推导的值是不是您预期的原因。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成中列出的更早版本相关的演练[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-run-a-program-in-debug-mode"></a>在调试模式下运行程序  
  
1.  打开 TestGames.cpp 以便进行编辑。  
  
2.  选择此代码行：  
  
     `Cardgame.solitaire(1);`  
  
3.  若要设置断点，在该一行，在菜单栏上，选择**调试**，**切换断点**，或按 F9 键。 行; 左侧显示一个红色圆圈它指示设置断点。 若要移除的断点，你可以选择菜单命令或 F9 键试。  
  
     如果你使用鼠标，还可以设置或通过单击左边距中移除的断点。  
  
4.  在菜单栏上，选择**调试**，**启动调试**，或选择 F5 键。  
  
     当程序到达具有断点的行时，将停止执行，因为程序处于中断模式。 代码行左侧的黄色箭头指示它是要执行的下一行。  
  
5.  若要检查的值`Cardgame::totalParticipants`变量，将指针移`Cardgame`，然后将它移动扩展控件在工具提示窗口的左侧。 变量名称`totalParticipants`并显示其值为 12。  
  
     打开的快捷菜单`Cardgame::totalParticipants`变量，然后选择**添加监视**以显示在该变量**监视 1**窗口。 此外可以选择一个变量，并将其拖到**监视 1**窗口。  
  
6.  若要单步执行到下一行代码，在菜单栏上，选择**调试**，**逐过程**，或选择 F10 键。  
  
     值`Cardgame::totalParticipants`中**监视 1**窗口现在显示为 13。  
  
7.  打开的快捷菜单`return 0;`语句，然后选择**运行到光标处**。 代码左侧的黄色箭头指向要执行的下一个语句。  
  
8.  `Cardgame::totalParticipants`数应减少 Cardgame 终止时。 此时，`Cardgame::totalParticipants`应等于 0，由于所有 Cardgame 实例已被都删除，但**监视 1**窗口指示`Cardgame::totalparticipants`等于 18。 这表示在代码中，你可以检测并修复通过完成下一个演练中，这是一个 bug[演练： 调试项目 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)。  
  
9. 若要停止该程序，在菜单栏上，选择**调试**，**停止调试**，或选择 Shift + F5 键盘快捷方式。  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：** [演练： 生成项目 （c + +）](../ide/walkthrough-building-a-project-cpp.md) &#124; **下一步：**[演练： 调试项目 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)