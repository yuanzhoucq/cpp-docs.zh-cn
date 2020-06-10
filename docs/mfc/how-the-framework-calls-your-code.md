---
title: 框架如何调用你的代码
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 318ca9558d705ca483d41867a1fe2ad46c36666f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622598"
---
# <a name="how-the-framework-calls-your-code"></a>框架如何调用你的代码

了解源代码和 MFC 框架中的代码之间的关系至关重要。 当应用程序运行时，大多数控件流位于框架的代码中。 框架管理一个消息循环，当用户在视图中选择命令和编辑数据时，此消息循环将会从 Windows 中获取消息。 框架可以单独处理的事件根本不用依赖您的代码。 例如，框架知道如何关闭窗口以及如何退出应用程序以响应用户命令。 在处理这些任务时，框架会使用消息处理程序和 C++ 虚函数，以便为你提供响应这些事件的机会。 但是，你的代码没有控制权，控制权在框架手中。

框架将会针对应用程序特定的事件调用你的代码。 例如，当用户选择某个菜单命令时，框架会将该命令传递给一系列 C++ 对象：当前视图和框架窗口、与当前视图关联的文档、文档的文档模板和应用程序对象。 如果其中某个对象可以处理命令，则会调用相应的消息处理程序函数来进行处理。 对于任何给定的命令，调用的代码可能是你的，也可能是框架的。

具有 Windows 的传统编程或事件驱动编程经验的程序员比较熟悉这种安排。

在相关主题中，您将会了解到，当框架初始化并运行应用程序时所做的工作，以及后来在应用程序终止时进行的清理工作。 你还将了解适合应用你编写的代码的位置。

有关详细信息，请参阅[类 CWinApp：应用程序类](cwinapp-the-application-class.md)和[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)。

## <a name="see-also"></a>另请参阅

[基于框架生成](building-on-the-framework.md)
