---
title: 演练： 生成项目 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c8d04dc3692076b867302af0e793eaac7ed25cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-building-a-project-c"></a>演练：生成项目 (C++)
在本演练中，你故意在代码中引入一个 Visual C++ 语法错误，来了解什么是编译错误，以及如何修复。 编译项目时，会显示错误消息以指示所发生的问题的性质和位置。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成中列出的更早版本相关的演练[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
### <a name="to-fix-compilation-errors"></a>修复编译错误  
  
1.  在 TestGames.cpp 中，删除最后一行中的分号，使代码如下所示：  
  
     `return 0`  
  
2.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
3.  中的消息**错误列表**窗口指示在生成项目时出错。 该声明类似于这样：  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     若要查看有关此错误的帮助信息，请突出显示在**错误列表**窗口，然后选择 F1 键。  
  
4.  将分号重新添加到导致语法错误的行的末尾：  
  
     `return 0;`  
  
5.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
     中的消息**输出**窗口指示项目已成功编译。  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Game.vcxproj -> C:\Users\<username>\Documents\Visual Studio <version>\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：** [演练： 使用项目和解决方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **下一步：**[演练： 测试项目 （c + +）](../ide/walkthrough-testing-a-project-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)