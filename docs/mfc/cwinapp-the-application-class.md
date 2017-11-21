---
title: "CWinApp： 应用程序类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46061c55bdf0bc8e6eb16a093fc8023c04939fa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cwinapp-the-application-class"></a>CWinApp：应用程序类
MFC 中的主应用程序类将封装 Windows 操作系统的应用程序的初始化、运行和终止。 基于框架生成的应用程序必须有且只有一个对象的类派生自[CWinApp](../mfc/reference/cwinapp-class.md)。 创建窗口之前将构造此对象。  
  
 `CWinApp` 派生自 `CWinThread`，它表示应用程序的执行的主线程（可能有一个或多个线程）。 在最新版本的 MFC， `InitInstance`，**运行**， `ExitInstance`，和`OnIdle`成员函数实际位于类`CWinThread`。 此处将这些函数作为 `CWinApp` 成员进行了讨论，因为讨论的焦点是将对象的角色视为应用程序对象，而不是主线程。  
  
> [!NOTE]
>  应用程序类构成了应用程序的执行主线程。 使用 Win32 API 函数，还可以创建执行的辅助线程。 这些线程可使用 MFC 库。 有关详细信息，请参阅[多线程处理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 与 Windows 操作系统的所有程序类似，框架应用程序具有 `WinMain` 函数。 但在框架应用程序中，您不编写 `WinMain`。 它由类库提供，并且在应用程序启动时调用。 `WinMain` 运行标准服务，如注册窗口类。 然后它调用应用程序对象的成员函数来初始化和运行该应用程序。 （您可通过重写 `WinMain` 调用的 `CWinApp` 成员函数来自定义 `WinMain`。）  
  
 若要初始化此应用程序，`WinMain` 将调用应用程序对象的 `InitApplication` 和 `InitInstance` 成员函数。 若要运行应用程序的消息循环，`WinMain`调用**运行**成员函数。 终止时，`WinMain` 将调用应用程序对象的 `ExitInstance` 成员函数。  
  
> [!NOTE]
>  名称中所示**粗体**本文档中指示由 Microsoft 基础类库和 Visual c + + 提供的元素。 以 `monospaced` 类型显示的名称表示您创建或重写的元素。  
  
## <a name="see-also"></a>另请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CWinApp 和 MFC 应用程序向导](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊的 CWinApp 服务](../mfc/special-cwinapp-services.md)

