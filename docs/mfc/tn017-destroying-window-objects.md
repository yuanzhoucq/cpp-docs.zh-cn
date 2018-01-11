---
title: "TN017： 销毁窗口对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.objects
dev_langs: C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d9aa4cabaafd4eebc3a0fb0b0023a82d446d74a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn017-destroying-window-objects"></a>TN017：销毁窗口对象
本说明介绍了利用[CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)方法。 使用此方法，如果你想要执行的自定义的分配`CWnd`-派生的对象。 本文还介绍了为何应使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)销毁而不是 c + + Windows 对象`delete`运算符。  
  
 如果您按照本主题中的准则，你将具有一些清理问题。 这些问题可以导致的问题，如忘记删除/释放 c + + 内存，忘记释放系统资源，如`HWND`s，或释放次数过多的对象。  
  
## <a name="the-problem"></a>问题  
 每个 windows 对象 (派生自的类的对象`CWnd`) 表示这两个 c + + 对象和`HWND`。 应用程序的堆中分配的 c + + 对象和`HWND`s 以系统资源分配的窗口管理器。 由于有几种销毁窗口对象的方法，我们必须提供一套规则，可防止系统资源或内存泄漏。 这些规则必须也阻止对象和 Windows 句柄正在销毁不止一次。  
  
## <a name="destroying-windows"></a>销毁窗口  
 销毁窗口对象的两种允许的方法如下：  
  
-   调用`CWnd::DestroyWindow`或 Windows API `DestroyWindow`。  
  
-   显式删除与`delete`运算符。  
  
 第一种情况是迄今最常见的。 这种情况下将应用，即使你的代码不调用`DestroyWindow`直接。 当用户直接关闭帧窗口时，此操作将生成`WM_CLOSE`消息，以及对此消息的默认响应是调用`DestroyWindow.`父窗口销毁时，Windows 会调用`DestroyWindow`其所有子项。  
  
 第二个用例、 使用`delete`Windows 对象运算符应该很少见。 某些情况下，使用以下是否`delete`是正确的选择。  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>与 CWnd::PostNcDestroy 自动清理  
 系统会销毁 Windows 窗口，发送到窗口的最后一个 Windows 消息时， `WM_NCDESTROY`。 默认值`CWnd`该消息的处理程序是[cwnd::](../mfc/reference/cwnd-class.md#onncdestroy)。 `OnNcDestroy`将分离`HWND`从 c + + 对象并调用虚函数`PostNcDestroy`。 一些类中重写此函数可删除 c + + 对象。  
  
 默认实现`CWnd::PostNcDestroy`不执行任何操作，这是适用于在堆栈帧上分配或嵌入其他对象的窗口对象。 这并不适合用于不包含任何其他对象在堆上分配的窗口对象。 换而言之，不适合于未嵌入在其他 c + + 对象的窗口对象。  
  
 重写这些类，旨在在堆上单独分配`PostNcDestroy`方法来执行`delete this`。 此语句将释放与 c + + 对象相关联的任何内存。 即使默认`CWnd`析构函数调用`DestroyWindow`如果`m_hWnd`为非 NULL，这不会导致无限递归因为句柄将分离和 NULL 在清除阶段。  
  
> [!NOTE]
>  系统通常在调用`CWnd::PostNcDestroy`它处理 Windows 后`WM_NCDESTROY`消息和`HWND`和 c + + 窗口对象无法再连接。 系统还将调用`CWnd::PostNcDestroy`大多数的实现中[cwnd:: Create](../mfc/reference/cwnd-class.md#create)调用，如果发生故障。 自动清除规则是在本主题后面所述。  
  
## <a name="auto-cleanup-classes"></a>自动清理类  
 以下类不用于自动清理。 它们通常被嵌入在其他 c + + 对象中或在堆栈上：  
  
-   所有标准 Windows 控件 (`CStatic`， `CEdit`， `CListBox`，依次类推)。  
  
-   直接从派生的任何子窗口`CWnd`（例如，自定义控件）。  
  
-   拆分窗口 (`CSplitterWnd`)。  
  
-   默认控件条 (类派生自`CControlBar`，请参阅[技术说明 31](../mfc/tn031-control-bars.md)用于启用自动删除控件条对象)。  
  
-   对话框 (`CDialog`) 设计的堆栈帧上的模式对话框。  
  
-   所有标准都对话框除外`CFindReplaceDialog`。  
  
-   创建的 ClassWizard 默认对话框。  
  
 以下类专门用于自动清理。 它们通常是在堆上分配本身：  
  
-   主框架窗口 (直接或间接派生自`CFrameWnd`)。  
  
-   查看 windows (直接或间接派生自`CView`)。  
  
 如果你想要中断这些规则，则必须重写`PostNcDestroy`方法在派生类中的。 若要将自动清理添加到你的类，调用基类，然后执行`delete this`。 若要从你的类中删除自动清理，请调用`CWnd::PostNcDestroy`而不是直接`PostNcDestroy`直接基类的方法。  
  
 更改自动清理行为的最常见用途是在堆上创建一个无模式对话框，可以分配。  
  
## <a name="when-to-call-delete"></a>为调用 delete 时  
 我们建议调用`DestroyWindow`销毁 Windows 对象，在 c + + 方法或全局`DestroyWindow`API。  
  
 不要调用全局`DestroyWindow`API 销毁 MDI 子窗口。 应使用的虚拟方法`CWnd::DestroyWindow`相反。  
  
 C + + 窗口对象，请不要执行自动清理，使用`delete`运算符可导致内存泄漏，当你尝试调用`DestroyWindow`中`CWnd::~CWnd`如果 VTBL 未指向正确派生的类的析构函数。 这是因为系统找不到相应 destroy 方法调用。 使用`DestroyWindow`而不是`delete`可避免这些问题。 因为这可能是一个细微的错误，在调试模式下进行编译将生成以下警告如果您就处于风险。  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 对于 c + + Windows 不要执行自动清理的对象，必须调用`DestroyWindow`。 如果你使用`delete`运算符直接，MFC 诊断内存分配器会通知你两次，你都将释放内存。 两个匹配项是你第一次的显式调用和间接调用`delete this`的自动清理实现中`PostNcDestroy`。  
  
 在调用`DestroyWindow`非自动清理对象的 c + + 对象仍将解决问题，但`m_hWnd`将为 NULL。 在调用`DestroyWindow`自动清理对象上的 c + + 对象将消失中的自动清理实现的 c + + delete 运算符释放`PostNcDestroy`。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

