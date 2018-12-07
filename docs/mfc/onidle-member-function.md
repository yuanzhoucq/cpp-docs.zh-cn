---
title: OnIdle 成员函数
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 7b3f2fbeac6ae356003abf12b5df4c54c8bb327a
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175128"
---
# <a name="onidle-member-function"></a>OnIdle 成员函数

正在处理任何 Windows 消息，框架将调用[CWinApp](../mfc/reference/cwinapp-class.md)成员函数[OnIdle](../mfc/reference/cwinapp-class.md#onidle) （MFC 库参考中所述）。

重写 `OnIdle` 以执行后台任务。 默认版本更新用户界面对象的状态（如工具栏按钮）并执行框架在其操作过程中创建的临时对象的清除。 下图演示消息循环如何在队列中没有消息时调用 `OnIdle`。

![消息循环过程](../mfc/media/vc387c1.gif "消息循环过程") <br/>
消息循环

可以在空闲循环中执行的操作的详细信息，请参阅[空闲循环处理](../mfc/idle-loop-processing.md)。

## <a name="see-also"></a>请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
