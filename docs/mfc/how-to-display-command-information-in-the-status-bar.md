---
title: 如何：在状态栏中显示命令信息
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: bff5d5b20ecc9b20b7b1e8335cda34d582441425
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622536"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>如何：在状态栏中显示命令信息

当你运行应用程序向导来创建应用程序的主干时，可以支持工具栏和状态栏。 应用程序向导中只有一个选项支持两者。 如果存在状态栏，则当用户将指针移到菜单上的项上方时，应用程序会自动提供有用的反馈。 突出显示菜单项时，应用程序会自动在状态栏中显示提示字符串。 例如，当用户将指针移到 "**编辑**" 菜单上的 "**剪切**" 命令上时，状态栏可能会在状态栏的消息区域中显示 "剪切选定内容并将其放在剪贴板上"。 该提示有助于用户了解菜单项的用途。 这也适用于用户单击工具栏按钮的情况。

可以通过为添加到程序的菜单项定义提示字符串，将添加到此状态栏帮助。 为此，请在菜单编辑器中编辑菜单项的属性时提供提示字符串。 你定义的字符串存储在应用程序资源文件中;它们具有与它们说明的命令相同的 Id。

默认情况下，应用程序向导添加**AFX_IDS_IDLEMESSAGE**，即标准 "Ready" 消息的 ID，该消息会在程序等待新消息时显示。 如果在应用程序向导中指定上下文相关帮助选项，则该消息将更改为 "获取帮助，请按 F1"。

## <a name="see-also"></a>另请参阅

[消息处理和映射](message-handling-and-mapping.md)
