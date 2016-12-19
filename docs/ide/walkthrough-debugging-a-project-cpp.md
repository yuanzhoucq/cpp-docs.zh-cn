---
title: "演练：调试项目 (C++) | Microsoft Docs"
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
  - "调试项目"
  - "项目调试 [C++]"
  - "项目 [C++], 调试"
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：调试项目 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本步骤中，您将调整程序以修复在测试项目时你所发现的问题。  
  
## 系统必备  
  
-   本演练假定您具备 C\+\+ 语言的基础知识。  
  
-   它还假定已完成[使用 Visual Studio IDE 进行 C\+\+ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的早期相关演练。  
  
### 修复包含 bug 的程序  
  
1.  要理解在撤销 `Cardgame` 对象时会发生什么, 请查看 `Cardgame` 类的析构函数。  
  
     在菜单栏上，选择“查看” 、“类似图” 。  
  
     在“类视图”  窗口中，展开“游戏”  项目树并选择“Cardgame”  类展示类成员和方法。  
  
     打开 **~Cardgame \(失效\)** 析构函数的快捷菜单然后选择“转到定义” 。  
  
2.  在卡片游戏终止时 `totalParticipants`会递减，请在析构函数 `Cardgame::~Cardgame` 的左大括号和右大括号之间加入以下代码：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  在您对 Cardgame.cpp 文件进行更改之后，该文件应类似于：  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
5.  在版本完成后，通过选择在菜单栏上的“调试”  “启动调试” 运行调试模式，或按 F5 键。  程序将在第一个断点处暂停。  
  
6.  若要逐句通过程序单步执行，则在菜单栏上，选择“调试” ，“单步执行” ，或选择 F10 键。  
  
     请注意，当卡片游戏的每个构造函数都执行后，`totalParticipants` 的值会增大。  当 `PlayGames` 函数返回，由于每个超出范围的卡片游戏实例都将被删除 \(并调用析构函数\)，`totalParticipants` 降低。  恰好在执行 `return` 语句之前，`totalParticipants` 等于 0。  
  
7.  继续逐句执行程序，直到退出或让其通过选择在菜单栏上的“调试” ，“运行” ，或通过选择 F5 键运行。  
  
## 后续步骤  
 **上一部分：** [演练：测试项目 \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **下一部分：**[演练：部署程序 \(C\+\+\)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-cn/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)