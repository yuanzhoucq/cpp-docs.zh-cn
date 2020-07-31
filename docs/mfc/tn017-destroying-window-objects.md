---
title: TN017：销毁窗口对象
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 2448a2661851f14fc6fe8747ca19495925442436
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226810"
---
# <a name="tn017-destroying-window-objects"></a>TN017：销毁窗口对象

本说明介绍了[CWnd：:P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法的用法。 如果要进行自定义的派生对象分配，请使用此方法 `CWnd` 。 此注释还说明了为什么应使用[CWnd：:D estroywindow](../mfc/reference/cwnd-class.md#destroywindow)销毁 c + + Windows 对象，而不是 **`delete`** 运算符。

如果遵循本主题中的准则，将会出现一些清理问题。 这些问题可能是由于以下问题引起的：忘记删除/释放 c + + 内存、忘记释放系统资源（如 `HWND` ），或释放对象的次数过多。

## <a name="the-problem"></a>问题

每个 windows 对象（派生自的类的对象 `CWnd` ）都表示 c + + 对象和 `HWND` 。 C + + 对象在应用程序的堆中分配，并 `HWND` 由窗口管理器在系统资源中分配。 由于有多种方法可以销毁窗口对象，因此我们必须提供一组阻止系统资源或内存泄漏的规则。 这些规则还必须阻止对象和 Windows 句柄被损坏多次。

## <a name="destroying-windows"></a>销毁 Windows

下面是两种销毁 Windows 对象的允许方法：

- 调用 `CWnd::DestroyWindow` 或 WINDOWS API `DestroyWindow` 。

- 用运算符显式删除 **`delete`** 。

第一种情况是最常见的一种情况。 即使您的代码不直接调用，这种情况也会适用 `DestroyWindow` 。 当用户直接关闭框架窗口时，此操作将生成 WM_CLOSE 消息，此消息的默认响应是 `DestroyWindow.` 在父窗口被销毁时调用，Windows 将调用 `DestroyWindow` 其所有子级。

第二种情况是，在 **`delete`** Windows 对象上使用运算符非常罕见。 下面是一些使用 **`delete`** 是正确选择的情况。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>通过 CWnd 自动清除：:P ostNcDestroy

当系统销毁 Windows 窗口时，将 WM_NCDESTROY 发送到窗口的最后一条 Windows 消息。 `CWnd`该消息的默认处理程序是[CWnd：： OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy`将 `HWND` 从 c + + 对象分离并调用虚拟函数 `PostNcDestroy` 。 某些类会重写此函数以删除 c + + 对象。

的默认实现 `CWnd::PostNcDestroy` 不执行任何操作，它适用于在堆栈帧上分配或嵌入到其他对象中的窗口对象。 这并不适合设计为在没有任何其他对象的情况下在堆上分配的窗口对象。 换句话说，它不适合于未嵌入其他 c + + 对象中的窗口对象。

那些设计为在堆上单独分配的类会重写 `PostNcDestroy` 方法，以执行**删除此**的。 此语句将释放与 c + + 对象关联的任何内存。 即使 `CWnd` `DestroyWindow` *M_HWND*为非 NULL，默认析构函数也会调用，这不会导致无限递归，因为句柄会在清理阶段分离和为 NULL。

> [!NOTE]
> 系统通常会 `CWnd::PostNcDestroy` 在处理 Windows WM_NCDESTROY 消息后调用 `HWND` ，并且不再连接 c + + 窗口对象。 如果发生故障，系统还会 `CWnd::PostNcDestroy` 在大多数[CWnd：： Create](../mfc/reference/cwnd-class.md#create)调用的实现中调用。 本主题后面部分介绍了自动清理规则。

## <a name="auto-cleanup-classes"></a>自动清理类

以下类不适合自动清除。 它们通常嵌入到其他 c + + 对象或堆栈上：

- 所有标准 Windows 控件（ `CStatic` 、 `CEdit` 、 `CListBox` 等）。

- 直接从派生的任何子窗口 `CWnd` （例如，自定义控件）。

- 拆分窗口（ `CSplitterWnd` ）。

- 默认控制条（派生自的类 `CControlBar` ，请参阅[技术说明 31](../mfc/tn031-control-bars.md) ，用于启用控件条对象的自动删除）。

- `CDialog`为堆栈帧上的模式对话框设计的对话框（）。

- 除之外的所有标准对话框 `CFindReplaceDialog` 。

- ClassWizard 创建的默认对话框。

以下类设计为自动清除。 它们通常在堆上自行分配：

- 主框架窗口（直接或间接派生自 `CFrameWnd` ）。

- 查看窗口（直接或间接从中派生 `CView` ）。

如果要中断这些规则，则必须 `PostNcDestroy` 在派生类中重写方法。 若要向类添加自动清理，请调用基类，然后执行**删除此**操作。 若要从类中删除自动清理，请 `CWnd::PostNcDestroy` 直接调用而不是 `PostNcDestroy` 直接基类的方法。

更改自动清理行为的最常见用途是创建可在堆上分配的无模式对话框。

## <a name="when-to-call-delete"></a>何时调用 delete

建议调用 `DestroyWindow` 以销毁 Windows 对象，即 c + + 方法或全局 `DestroyWindow` API。

不要调用全局 `DestroyWindow` API 来销毁 MDI 子窗口。 应改用虚方法 `CWnd::DestroyWindow` 。

对于不执行自动清除的 c + + 窗口对象， **`delete`** `DestroyWindow` `CWnd::~CWnd` 如果 VTBL 未指向正确的派生类，则当您尝试在析构函数中调用时，使用运算符可能会导致内存泄漏。 出现这种情况的原因是系统找不到合适的销毁方法来调用。 使用 `DestroyWindow` 而不是 **`delete`** 避免出现这些问题。 由于这可能是一个微妙的错误，因此，在调试模式下编译将生成以下警告（如果您面临风险）。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

对于执行自动清除的 c + + Windows 对象，您必须调用 `DestroyWindow` 。 如果 **`delete`** 直接使用运算符，则 MFC 诊断内存分配器会通知你要释放两次内存。 这两个实例是第一次显式调用，以及用于在的自动清理实现中**删除此**的间接调用 `PostNcDestroy` 。

`DestroyWindow`对非自动清除对象调用之后，c + + 对象仍将继续，但*m_hWnd*将为 NULL。 `DestroyWindow`在自动清理对象上调用后，c + + 对象将不再由的自动清理实现中的 c + + delete 运算符释放 `PostNcDestroy` 。

## <a name="see-also"></a>另请参阅

[按编号的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
