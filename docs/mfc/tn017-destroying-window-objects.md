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
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370424"
---
# <a name="tn017-destroying-window-objects"></a>TN017：销毁窗口对象

本说明描述了[CWnd：:PostNc销毁方法](../mfc/reference/cwnd-class.md#postncdestroy)的使用。 如果要对派生对象进行自定义分配，`CWnd`请使用此方法。 此注释还解释了为什么应该使用[CWnd：:DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)销毁C++ Windows 对象而不是**删除**运算符。

如果您遵循本主题中的指南，则将几乎没有清理问题。 这些问题可能由忘记删除/释放C++内存、忘记释放系统资源（如 s）`HWND`或释放对象的次数过多等问题导致。

## <a name="the-problem"></a>问题

每个窗口对象（派生自`CWnd`的类的对象）都表示C++对象和 。 `HWND` C++对象在应用程序的堆中分配，`HWND`并且窗口管理器在系统资源中分配。 由于有几种方法可以销毁窗口对象，因此我们必须提供一组规则来防止系统资源或内存泄漏。 这些规则还必须防止对象和 Windows 句柄被销毁一次以上。

## <a name="destroying-windows"></a>销毁窗口

以下是销毁 Windows 对象的两种允许方法：

- 调用`CWnd::DestroyWindow`或 Windows `DestroyWindow`API 。

- 使用**删除**运算符显式删除。

第一种情况是迄今为止最常见的。 即使您的代码不直接调用`DestroyWindow`，此情况也适用。 当用户直接关闭框架窗口时，此操作将生成WM_CLOSE消息，对此消息的默认响应是调用`DestroyWindow.`"当父窗口被销毁时，Windows 会调用`DestroyWindow`其所有子级"。

第二种情况是**删除运算符在**Windows 对象上使用的情况应该很少。 以下是使用**删除**的正确选择。

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>使用 CWnd 自动清理：:PostNc销毁

当系统破坏 Windows 窗口时，发送到该窗口的最后一个 Windows 消息将WM_NCDESTROY。 该消息`CWnd`的默认处理程序是[CWnd：：onNc销毁](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy`将从C++对象`HWND`分离，并调用虚拟函数`PostNcDestroy`。 某些类重写此函数以删除C++对象。

的`CWnd::PostNcDestroy`默认实现不执行任何操作，这适用于在堆栈框架上分配或嵌入到其他对象中的窗口对象。 这不适用于设计为在堆上分配而不分配任何其他对象的窗口对象。 换句话说，它不适用于未嵌入到其他C++对象的窗口对象。

那些设计为单独在堆上分配的类重写`PostNcDestroy`方法以执行**删除此**。 此语句将释放与C++对象关联的任何内存。 即使默认`CWnd`析构函数调用`DestroyWindow`，如果*m_hWnd*是非 NULL，这也不会导致无限递归，因为句柄将在清理阶段分离和 NULL。

> [!NOTE]
> 系统通常在处理`CWnd::PostNcDestroy`Windows WM_NCDESTROY 消息后调用，`HWND`并且 C++窗口对象不再连接。 系统还将调用`CWnd::PostNcDestroy`大多数[CWnd：：：如果发生故障，创建](../mfc/reference/cwnd-class.md#create)调用。 本主题稍后将介绍自动清理规则。

## <a name="auto-cleanup-classes"></a>自动清理类

以下类不是为自动清理而设计的。 它们通常嵌入到其他C++对象或堆栈中：

- 所有标准 Windows`CStatic`控件`CEdit` `CListBox`（、、等）。

- 直接派生自`CWnd`的任何子窗口（例如，自定义控件）。

- 拆分窗口 （`CSplitterWnd`。

- 默认控制栏（派生自`CControlBar`的类，请参阅[技术说明 31，](../mfc/tn031-control-bars.md)用于启用控件栏对象的自动删除）。

- 为堆栈`CDialog`帧上的模式对话框设计的对话框 （ ）

- 除`CFindReplaceDialog`之外的所有标准对话框。

- 类向导创建的默认对话框。

以下类专为自动清理而设计。 它们通常由堆上自己分配：

- 主框架窗口（直接或间接派生自`CFrameWnd`）。

- 查看窗口（直接或间接派生自`CView`）。

如果要破坏这些规则，则必须重写派生类中`PostNcDestroy`的方法。 要向类添加自动清理，请调用基类，然后删除**此**。 要从类中删除自动清理，请直接调用`CWnd::PostNcDestroy`而不是直接基类`PostNcDestroy`的方法。

更改自动清理行为的最常见用途是创建可在堆上分配的无模式对话框。

## <a name="when-to-call-delete"></a>何时调用删除

我们建议您调用`DestroyWindow`以销毁 Windows 对象，C++ 方法或全局`DestroyWindow`API。

不要调用全局`DestroyWindow`API 来销毁 MDI 子窗口。 您应该改用虚拟方法`CWnd::DestroyWindow`。

对于不执行自动清理的C++窗口对象，如果 VTBL 未指向正确派生的类，则当您尝试`DestroyWindow`调用`CWnd::~CWnd`析构函数时，使用**delete**运算符可能会导致内存泄漏。 这是因为系统找不到要调用的适当销毁方法。 使用`DestroyWindow`而不是**删除**可以避免这些问题。 由于这可能是一个微妙的错误，因此，如果您处于危险之中，在调试模式下编译将生成以下警告。

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

如果C++执行自动清理的 Windows 对象，则必须调用`DestroyWindow`。 如果您直接使用**删除**运算符，MFC 诊断内存分配器将通知您释放内存两次。 这两个事件是您的第一个显式调用，以及间接调用，用于在 自动清理实现中删除`PostNcDestroy`**此调用**。

调用`DestroyWindow`非自动清理对象后，C++对象仍将在周围，但*m_hWnd*将为 NULL。 调用`DestroyWindow`自动清理对象后，C++对象将消失，由C++删除运算符在 自动清理实现中`PostNcDestroy`释放。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
