---
title: 演练：测试项目 (C++) | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333559"
---
# <a name="walkthrough-testing-a-project-c"></a>演练：测试项目 (C++)
在调试模式下运行程序时，可使用断点来暂停程序以检查变量和对象的状态。  
  
 在本演练中，将在程序运行时观察变量的值，并推导出为什么该值不是期望的值。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成之前在[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的相关演练。  
  
### <a name="to-run-a-program-in-debug-mode"></a>在调试模式下运行程序  
  
1.  打开 TestGames.cpp 进行编辑。  
  
2.  选择此代码行：  
  
     `Cardgame.solitaire(1);`  
  
3.  要在该行上设置断点，请在菜单栏上选择“调试”、“切换断点”，或选择 F9 键。 行的左侧出现一个红色圆圈，它表示已设置断点。 要删除断点，可再次选择菜单命令或 F9 键。  
  
     如果使用鼠标，也可通过单击左边距来设置或删除断点。  
  
4.  在菜单栏上，依次选择“调试”、“启动调试”，或选择 F5 键。  
  
     程序到达具有断点的行时，暂时停止执行，因为程序处于中断模式。 代码行左侧的黄色箭头表示它是要执行的下一行。  
  
5.  要检查变量 `Cardgame::totalParticipants` 的值，请将指针移到 `Cardgame` 上，然后将其移到工具提示窗口左侧的扩展控件上。 显示变量名称 `totalParticipants` 及其值 12。  
  
     打开变量 `Cardgame::totalParticipants` 的快捷菜单，然后选择“添加监视”以在“监视 1”窗口中显示该变量。 也可选择一个变量并将其拖动到“监视 1”窗口。  
  
6.  要转到下一代码行，请在菜单栏上依次选择“调试”、“逐过程执行”或选择 F10 键。  
  
     “监视 1”窗口中 `Cardgame::totalParticipants` 的值现在显示为 13。  
  
7.  打开 `return 0;` 语句的快捷菜单，然后选择“运行到光标处”。 代码左侧的黄色箭头指向要执行的下一语句。  
  
8.  Cardgame 终止时，`Cardgame::totalParticipants` 数应减少。 此时，`Cardgame::totalParticipants` 应等于 0，因为已删除所有 Cardgame 实例，但“监视 1”窗口指示 `Cardgame::totalparticipants` 等于 18。 这表明代码中存在 bug，可通过完成下一个演练（[演练：调试项目 (C++)](../ide/walkthrough-debugging-a-project-cpp.md)）来检测和修复该 bug。  
  
9. 要停止该程序，请在菜单栏上选择“调试”、“停止调试”或选择 Shift+F5 键盘快捷方式。  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：**[演练：生成项目 (C++)](../ide/walkthrough-building-a-project-cpp.md) | **下一步：**[演练：调试项目 (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)