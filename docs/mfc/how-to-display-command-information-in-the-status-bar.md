---
title: 如何：在状态栏中显示命令信息
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: c93787b3799306d6008299e7c1be6e429bc4c2d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282313"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>如何：在状态栏中显示命令信息

当您运行应用程序向导创建的应用程序框架时，可以支持一个工具栏和状态栏。 两者都支持应用程序向导中的一个选项。 存在一个状态栏，则该应用程序将自动提供有用的反馈，用户将指针移动到项，菜单上。 应用程序会自动突出显示的菜单项时在状态栏中显示提示字符串。 例如，当用户将指针移动**剪切**命令**编辑**菜单中，状态栏可能会在消息区域中的状态栏中显示"剪切所选内容并将其放到剪贴板上"。 在提示符下帮助用户理解的菜单项的用途。 这一点同样适用当用户单击的工具栏按钮。

可以通过定义添加到程序的菜单项的提示字符串添加到此状态栏帮助。 若要执行此操作，请编辑菜单编辑器中的菜单项的属性时提供的提示字符串。 您定义的字符串存储在应用程序资源文件;它们具有相同的 Id 的命令，它们介绍了。

默认情况下，应用程序向导将添加**AFX_IDS_IDLEMESSAGE**，标准的"准备"消息，当程序正在等待新消息时显示的 ID。 如果应用程序向导中指定的上下文相关帮助选项，该消息更改为"的帮助，请按 F1。"

## <a name="see-also"></a>请参阅

[消息处理和映射](../mfc/message-handling-and-mapping.md)
