---
title: 演练：调试项目 (C++)
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: ce792345b045a1e647de6363ca094fb3f3826b73
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400981"
---
# <a name="walkthrough-debugging-a-project-c"></a>演练：调试项目 (C++)

在本演练中，你将修改程序以修复在测试项目时发现的问题。

## <a name="prerequisites"></a>系统必备

- 本演练假定你具备 C++ 语言的基础知识。

- 它还假定你已完成之前在[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的相关演练。

### <a name="to-fix-a-program-that-has-a-bug"></a>修复含有 bug 的程序

1. 若要查看销毁 `Cardgame` 对象时发生的情况，请查看 `Cardgame` 类的析构函数。

   在菜单栏上，选择“视图”   > “类视图”  。

   在“类视图”窗口中，展开“游戏”项目树并选择“Cardgame”类来显示类成员和方法    。

   打开“~Cardgame(void)”析构函数的快捷菜单，然后选择“转到定义”   。

1. 若要在 Cardgame 终止时减少 `totalParticipants`，请在 `Cardgame::~Cardgame` 析构函数的左大括号和右大括号之间键入以下代码。

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. 在对 Cardgame.cpp 文件进行更改之后，该文件应类似于以下代码：

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. 在菜单栏上，依次选择“生成” > “生成解决方案”   。

1. 生成完成后，可以通过选择菜单栏上的“调试”   > “启动调试”  或选择 F5  键在调试模式下运行此解决方案。 程序在第一个断点处暂停程序。

1. 若要逐步执行此程序，请在菜单栏上，选择“调试”   > “逐过程执行”  或选择 F10  键。

   请注意，执行每个 `Cardgame` 构造函数后，`totalParticipants` 的值会增大。 在 `PlayGames` 函数返回时，由于每个 `Cardgame` 实例都超出范围且被删除（并且调用析构函数），因此 `totalParticipants` 会减小。 在刚要执行 `return` 语句前，`totalParticipants` 等于 0。

1. 继续逐步执行此程序直到其退出，或通过在菜单栏上选择“调试”   > “运行”  或选择 F5  键来使其运行。

## <a name="next-steps"></a>后续步骤

上一步：  [演练：测试项目 (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**下一篇：** [演练：部署程序 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](../build/projects-and-build-systems-cpp.md)<br/>
