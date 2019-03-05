---
title: TN017:销毁窗口对象
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 9e52112bed0f583a3f5652f9213bd5049d543a80
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294105"
---
# <a name="tn017-destroying-window-objects"></a>TN017:销毁窗口对象

本说明介绍如何使用[CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法。 使用此方法，如果你想要执行的自定义的分配`CWnd`-派生的对象。 本说明还说明了为何应使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)要销毁的 c + + Windows 对象而不是**删除**运算符。

如果遵循本主题中的指导原则，将具有一些清理问题。 这些问题可以造成的问题，如忘记删除/释放 c + + 内存，忘记释放系统资源，如`HWND`s，或释放次数过多的对象。

## <a name="the-problem"></a>问题

每个 windows 对象 (类的对象派生自`CWnd`) 表示这两个 c + + 对象和一个`HWND`。 C + + 对象在应用程序的堆中分配和`HWND`s 中的系统资源分配窗口管理器。 有几种方法来销毁窗口对象，因为我们必须提供一套规则，可防止系统资源或内存泄漏。 这些规则必须也阻止对象和 Windows 句柄处于销毁不止一次。

## <a name="destroying-windows"></a>销毁 Windows

若要销毁 Windows 对象的两种允许的方法如下：

- 调用`CWnd::DestroyWindow`或 Windows API `DestroyWindow`。

- 使用显式删除**删除**运算符。

第一种情况是到目前为止最常见的。 即使你的代码不会调用这种情况下适用`DestroyWindow`直接。 当用户直接关闭框架窗口，此操作将生成 WM_CLOSE 消息，且默认响应此消息是调用`DestroyWindow.`当父窗口被破坏时，Windows 会调用`DestroyWindow`其所有子项。

第二种情况，使用**删除**运算符对 Windows 对象应该很少见。 某些情况下，使用以下内容**删除**是正确的选择。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>使用 CWnd::PostNcDestroy 自动清理

系统会销毁 Windows 窗口，发送到窗口的最后一个 Windows 消息时，WM_NCDESTROY。 默认值`CWnd`，该消息的处理程序是[cwnd:: Onncdestroy](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy` 将分离`HWND`通过 c + + 对象并调用虚函数`PostNcDestroy`。 一些类重写此函数可删除 c + + 对象。

默认实现`CWnd::PostNcDestroy`不执行任何操作，这是适用于在堆栈帧上分配或嵌入到其他对象中的窗口对象。 这并不适合用于不包含任何其他对象在堆上分配的窗口对象。 换而言之，不适合于未嵌入在其他 c + + 对象的窗口对象。

专为在堆上单独分配这些类重写`PostNcDestroy`方法来执行**删除此**。 此语句将释放与 c + + 对象相关联的任何内存。 即使默认`CWnd`析构函数调用`DestroyWindow`如果*m_hWnd*为非 NULL，这不会导致无限递归因为句柄将清理阶段会分离和 NULL。

> [!NOTE]
>  系统通常会调用`CWnd::PostNcDestroy`处理 Windows WM_NCDESTROY 消息后和`HWND`和断开连接的 c + + 窗口对象。 系统还将调用`CWnd::PostNcDestroy`中的大多数实现[cwnd:: Create](../mfc/reference/cwnd-class.md#create)失败时调用。 自动清理规则是在本主题后面所述。

## <a name="auto-cleanup-classes"></a>自动清理类

以下类并不设计用于自动清理。 它们通常都被嵌入其他 c + + 对象中或在堆栈上：

- 所有标准 Windows 控件 (`CStatic`， `CEdit`， `CListBox`，依此类推)。

- 直接从任何子窗口派生`CWnd`（例如，自定义控件）。

- 拆分窗口 (`CSplitterWnd`)。

- 默认控件条 (类派生自`CControlBar`，请参阅[技术说明 31](../mfc/tn031-control-bars.md)用于启用自动删除控件条对象)。

- 对话框 (`CDialog`) 设计模式对话框上的堆栈帧的。

- 除了所有标准都对话框`CFindReplaceDialog`。

- 创建的类向导默认对话框。

以下类旨在自动清理。 它们通常是在堆上分配本身：

- 主框架窗口 (直接或间接派生自`CFrameWnd`)。

- 查看 windows (直接或间接派生自`CView`)。

如果你想要中断这些规则，则必须重写`PostNcDestroy`派生类中的方法。 若要添加到您的类自动清理，请调用基类，然后执行**删除此**。 若要从您的类中删除自动清理，请调用`CWnd::PostNcDestroy`而不是直接`PostNcDestroy`直接基类的方法。

更改自动清理行为的最常见的用途是在堆上创建一个无模式对话框，可以分配。

## <a name="when-to-call-delete"></a>为调用 delete 时

我们建议您调用`DestroyWindow`销毁 Windows 对象，在 c + + 方法或全局`DestroyWindow`API。

不要调用全局`DestroyWindow`API 要销毁的 MDI 子窗口。 应使用的虚拟方法`CWnd::DestroyWindow`相反。

C + + 窗口对象不执行自动清理，使用**删除**当你尝试调用时，运算符可能会导致内存泄漏`DestroyWindow`中`CWnd::~CWnd`如果 VTBL 不指向正确派生的类的析构函数。 这是因为系统无法找到相应 destroy 方法调用。 使用`DestroyWindow`而不是**删除**可避免这些问题。 因为这可能是一个细微的错误，在调试模式下进行编译将生成以下警告如果您是有风险。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

对于执行自动清理的 c + + Windows 对象，必须调用`DestroyWindow`。 如果您使用**删除**运算符直接，MFC 诊断内存分配器会通知您两次，您都将释放内存。 两个匹配项是你第一次的显式调用和对的间接调用**删除此**中的自动清理实现`PostNcDestroy`。

在调用`DestroyWindow`非自动清理对象上的 c + + 对象仍会但*m_hWnd*将为 NULL。 在调用`DestroyWindow`自动清理对象后，c + + 对象将被删除，释放由 c + + delete 运算符中的自动清理实现`PostNcDestroy`。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
