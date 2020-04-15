---
title: CWinApp：应用程序类
ms.date: 11/04/2016
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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373527"
---
# <a name="cwinapp-the-application-class"></a>CWinApp：应用程序类

MFC 中的主应用程序类将封装 Windows 操作系统的应用程序的初始化、运行和终止。 构建在框架上的应用程序必须具有从[CWinApp](../mfc/reference/cwinapp-class.md)派生的类的一个对象。 创建窗口之前将构造此对象。

`CWinApp` 派生自 `CWinThread`，它表示应用程序的执行的主线程（可能有一个或多个线程）。 在 MFC 的最新版本中`InitInstance`， **Run**运行`ExitInstance`和`OnIdle`成员函数实际上是在类`CWinThread`中。 此处将这些函数作为 `CWinApp` 成员进行了讨论，因为讨论的焦点是将对象的角色视为应用程序对象，而不是主线程。

> [!NOTE]
> 应用程序类构成了应用程序的执行主线程。 使用 Win32 API 函数，还可以创建执行的辅助线程。 这些线程可使用 MFC 库。 有关详细信息，请参阅[多线程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

与 Windows 操作系统的所有程序类似，框架应用程序具有 `WinMain` 函数。 但在框架应用程序中，您不编写 `WinMain`。 它由类库提供，并且在应用程序启动时调用。 `WinMain` 运行标准服务，如注册窗口类。 然后它调用应用程序对象的成员函数来初始化和运行该应用程序。 （您可通过重写 `WinMain` 调用的 `CWinApp` 成员函数来自定义 `WinMain`。）

若要初始化此应用程序，`WinMain` 将调用应用程序对象的 `InitApplication` 和 `InitInstance` 成员函数。 要运行应用程序的消息循环，`WinMain`请调用**Run**成员函数。 终止时，`WinMain` 将调用应用程序对象的 `ExitInstance` 成员函数。

> [!NOTE]
> 本文档中**以粗体**显示的名称表示 Microsoft 基础类库和可视化C++提供的元素。 以 `monospaced` 类型显示的名称表示您创建或重写的元素。

## <a name="see-also"></a>另请参阅

[一般 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[CWinApp 和 MFC 应用程序向导](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)<br/>
[特别 CWinApp 服务](../mfc/special-cwinapp-services.md)
