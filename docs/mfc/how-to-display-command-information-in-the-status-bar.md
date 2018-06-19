---
title: 如何： 在状态栏中显示命令信息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 440e550e6e1ba5a82cac3f35dcb3c76b346b5343
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346040"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>如何：在状态栏中显示命令信息
当你运行应用程序向导创建主干应用程序时，可以支持一个工具栏和状态栏。 两者都支持应用程序向导中的一个选项。 当存在时状态栏时，则应用程序都将自动提供有用的反馈，用户将指针移动到项，在菜单上。 应用程序突出显示菜单项时，自动将提示字符串显示在状态栏中。 例如，当用户将指针移动**剪切**命令**编辑**菜单上，状态栏可能会在消息区域中的状态栏中显示"剪切所选内容并将其放在剪贴板上"。 在提示符下，从而帮助用户了解的菜单项的用途。 此方法也适用当用户单击工具栏按钮。  
  
 可以通过定义菜单项添加到程序的提示字符串添加到此状态栏帮助。 若要执行此操作，提供提示字符串时编辑菜单编辑器中的菜单项的属性。 你定义的字符串存储在应用程序资源文件;它们具有同一 Id 作为它们说明的命令。  
  
 默认情况下，应用程序向导添加`AFX_IDS_IDLEMESSAGE`，标准的"准备"消息，该程序正在等待新消息时，将显示的 ID。 如果在应用程序向导中指定的上下文相关帮助选项，消息将变为"帮助，请按 F1。"  
  
## <a name="see-also"></a>请参阅  
 [消息处理和映射](../mfc/message-handling-and-mapping.md)

