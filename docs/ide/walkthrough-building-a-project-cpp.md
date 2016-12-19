---
title: "演练：生成项目 (C++) | Microsoft Docs"
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
  - "生成项目 [C++]"
  - "项目 [C++]，生成"
  - "项目生成 [C++]"
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：生成项目 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本演练中，你故意在代码中引入一个 Visual C\+\+ 语法错误，来了解什么是编译错误，以及如何修复。  编译项目时，会显示错误消息以指示所发生的问题的性质和位置。  
  
## 系统必备  
  
-   本演练假定你具备 C\+\+ 语言的基础知识。  
  
-   它还假定你已完成[使用 Visual Studio IDE 进行 C\+\+ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的早期相关演练。  
  
### 修复编译错误  
  
1.  在 TestGames.cpp 中，删除最后一行中的分号，使代码如下所示：  
  
     `return 0`  
  
2.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
3.  **“错误列表”**窗口中的消息表示生成项目过程中出现了错误。  该声明类似于这样：  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     若要查看有关此错误的帮助信息，请在**“错误列表”**窗口中将其选中，然后按 F1 键。  
  
4.  将分号重新添加到导致语法错误的行的末尾：  
  
     `return 0;`  
  
5.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
     **“输出”**窗口中显示一条消息，指示项目已成功编译。  
  
  **1\>\-\-\-\-\-\- 生成已开始: 项目: Game, 配置: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Game.vcxproj \-\> C:\\Users\\\<用户名\>\\Documents\\Visual Studio *\<version\>*\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= 生成: 1 成功, 0 失败, 0 最新, 0 被跳过 \=\=\=\=\=\=\=\=\=\=**  
  
## 后续步骤  
 **上一部分：** [演练：使用项目和解决方案 \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **下一部分：** [演练：测试项目 \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/zh-cn/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)