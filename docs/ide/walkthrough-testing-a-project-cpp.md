---
title: "演练：测试项目 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "项目测试 [C++]"
  - "项目 [C++], 测试"
  - "测试项目"
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：测试项目 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以“调试”模式运行程序时，您可以使用断点来暂停程序，以检查变量和对象的状态。  
  
 在本演练中，您在程序运行时观察变量的值，并推断为什么值与预期不同。  
  
## 系统必备  
  
-   本演练假定您具备 C\+\+ 语言的基础知识。  
  
-   它还假定已完成[使用 Visual Studio IDE 进行 C\+\+ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的早期相关演练。  
  
### 以“调试”模式运行程序  
  
1.  打开 TestGames.cpp 进行编辑。  
  
2.  选择此行代码：  
  
     `Cardgame.solitaire(1);`  
  
3.  若要在该行上设置断点，请在菜单栏上依次选择“调试”、“切换断点”，或者按 F9 键。  该行的左侧会显示一个红色圆圈；此圆圈表示设置了断点。  若要移除断点，您可以再次选择菜单命令或按 F9 键。  
  
     如果您使用鼠标，则可以通过单击左侧边距来设置或移除断点。  
  
4.  在菜单栏上，依次选择“调试”、“启动调试”，或按 F5 键。  
  
     当程序运行到包含断点的行时，执行将暂时停止（因为程序处于“中断”模式）。  代码行左侧的黄色箭头指示该行是要执行的下一个代码行。  
  
5.  若要检查变量 `Cardgame::totalParticipants` 的值，请将指针移到 `Cardgame` 上，然后再将指针移到工具提示窗口左侧的扩展控件上。  将显示变量的名称 `totalParticipants` 和其值 12。  
  
     打开 `Cardgame::totalParticipants` 变量的快捷菜单，然后选择“添加监视”在“监视 1”窗口中显示变量。  您也可以选择该变量并将其拖动到“监视 1”窗口。  
  
6.  若要步进到下一行代码，请在菜单栏上依次选择“调试”、“单步执行”，或者按 F10 键。  
  
     “监视 1”窗口中 `Cardgame::totalParticipants` 的值现在显示为 13。  
  
7.  打开 `return 0;` 语句的快捷菜单，然后选择“运行到光标处”。  代码左侧的黄色箭头指向要执行的下一个语句。  
  
8.  当 Cardgame 终止时，`Cardgame::totalParticipants` 数应减少。  此时，`Cardgame::totalParticipants` 应为 0，原因在于所有的 Cardgame 实例都已删除，但“监视 1”窗口显示 `Cardgame::totalparticipants` 等于 18。  这表明代码中有 Bug，而您可以通过完成下一个演练来对其进行检测和修复，[演练：调试项目 \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)。  
  
9. 若要停止程序，请在菜单栏上选择“调试”、“停止调试”或按 Shift\+F5 键盘快捷键。  
  
## 后续步骤  
 **上一部分：** [演练：生成项目 \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md) &#124; **下一部分：**[演练：调试项目 \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-cn/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)