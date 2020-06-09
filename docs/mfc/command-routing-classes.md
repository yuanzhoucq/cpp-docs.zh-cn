---
title: 命令传送类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d7ff275d373cf50ab8ebe52ed454bd25cd473e11
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624828"
---
# <a name="command-routing-classes"></a>命令传送类

当用户通过用鼠标选择菜单或控件条按钮与应用程序交互时，应用程序会将来自受影响的用户界面对象的消息发送到合适的命令目标对象。 派生自的命令目标类 `CCmdTarget` 包括[CWinApp](reference/cwinapp-class.md)、 [CWnd](reference/cwnd-class.md)、 [CDocTemplate](reference/cdoctemplate-class.md)、 [CDocument](reference/cdocument-class.md)、 [CView](reference/cview-class.md)以及从它们派生的类。 框架支持自动命令传送，以便让命令可以由应用程序中当前处于活动状态的最合适的对象处理。

类的对象 `CCmdUI` 将传递给命令目标的更新命令 UI （[ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)）处理程序，使您可以更新特定命令的用户界面状态（例如，检查或删除菜单项中的检查）。 您可调用 `CCmdUI` 对象的成员函数以更新 UI 对象的状态。 无论与特定命令关联的 UI 对象是菜单项、按钮还是这两者，此过程都是相同。

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
充当可接收和响应消息的所有对象类的基类的服务。

[CCmdUI](reference/ccmdui-class.md)<br/>
提供用于更新用户界面对象（如菜单项或控件条按钮）的编程接口。 命令目标对象启用、禁用、检查和/或清除带有此对象的用户界面对象。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
