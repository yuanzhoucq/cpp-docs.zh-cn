---
title: "TN017：销毁窗口对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "销毁窗口"
  - "PostNcDestroy 方法"
  - "TN017"
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN017：销毁窗口对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明使用 [CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) 方法。  如果要执行的自定义的 `CWnd`分配派生的对象，请使用此方法。  此注释还说明您为什么使用 [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) 销毁 C\+\+. Windows 窗体对象而不是 `delete` 运算符。  
  
 如果您遵守本主题中的准则，您会具有较少形清理问题。  这些问题可能会导致问题，例如忘记删除\/免费的C\+ \+内存，像`HWND`免费的系统资源，或者释放对象的次数太多。  
  
## 问题  
 每个窗口对象 \(从 `CWnd`派生的类的对象。\) 表示两个 C.C\+\+ 对象和 `HWND`。  C\+\+ 对象在应用程序内存段分配，并在 `HWND`中分配由 Windows 系统资源管理器。  由于有多种方式销毁窗口对象，我们必须提供防止系统资源或内存泄漏的一组规则。  这些规则还必须防止对象和窗口句柄被销毁多次。  
  
## 销毁窗口  
 下面是两个允许方式销毁窗口对象：  
  
-   调用 `CWnd::DestroyWindow` 或 Windows API `DestroyWindow`。  
  
-   显式删除使用 `delete` 运算符。  
  
 第一个用例 \(这是迄今为止最常见。  此情况下应用，即使代码不直接调用 `DestroyWindow`。  如果用户直接关闭一框架窗口时，此操作将生成消息 `WM_CLOSE`，这样，到此消息的默认响应是调用 `DestroyWindow.` ，则销毁时父窗口，窗口中调用其所有子级的 `DestroyWindow`。  
  
 第二种情况，请使用窗口的 `delete` 运算符对象，应该很少见的。  以下是使用 `delete` 的情形是正确的选择。  
  
## 与 CWnd::PostNcDestroy 的自动清理  
 当系统窗口销毁一个窗口时，窗口上发送到 Windows 为 `WM_NCDESTROY`。  该消息的默认 `CWnd` 处理程序为 [CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)。  `OnNcDestroy` 将分离从 C\+\+ 对象的 `HWND` 并调用虚函数 `PostNcDestroy`。  这些类中替代此函数删除 C\+\+ 对象。  
  
 `CWnd::PostNcDestroy` 的默认实现不执行任何操作，提供窗口对象 \(在堆栈帧在分配或嵌入其他对象。  这对于在堆中分配，且不包含任何其他对象的设计窗口对象不正确。  换言之，用于其他 C\+\+ 对象未嵌入的窗口对象不正确。  
  
 堆上重写中单独的分配方式执行 `delete this`的 `PostNcDestroy` 方法的类。  此语句将释放任何内存与 C\+\+ 对象。  即使默认 `CWnd` 析构函数调用 `DestroyWindow`，如果 `m_hWnd` 不为 null，这不导致无限递归，因为在处理清理阶段是分离并 NULL。  
  
> [!NOTE]
>  系统调用 `CWnd::PostNcDestroy`，通常在处理 Windows 消息 `WM_NCDESTROY` 后，`HWND` 对象和 C\+\+ Windows 不再连接。  如果失败，系统还将调用在大多数调用 [CWnd::Create](../Topic/CWnd::Create.md) 的实现的 `CWnd::PostNcDestroy`。  自动清理规则将在本主题后面进行介绍。  
  
## 自动清理类  
 下列类不会自动清理设计。  它们通常嵌入到其他 C\+\+ 对象或在堆栈：  
  
-   所有标准 Windows 控件 \(`CStatic`、`CEdit`，`CListBox`，依此类推\)。  
  
-   直接从 `CWnd` 派生的任何子窗口 \(例如，自定义控件\)。  
  
-   拆分窗口 \(`CSplitterWnd`\)。  
  
-   默认控制条 \(从 `CControlBar`派生的类，该类使控制条的对象自动删除参见 [技术说明 31](../mfc/tn031-control-bars.md) \)。  
  
-   对堆栈帧上的模式对话框 \(`CDialog`\) 的对话框。  
  
-   所有标准对话框中除 `CFindReplaceDialog`。  
  
-   ClassWizard 创建的默认对话框。  
  
 下列类会自动清理设计。  它们通常在单独堆分配：  
  
-   主框架窗口 \(直接或间接从 `CFrameWnd`派生\)。  
  
-   窗口 \(直接或间接从 `CView`派生\)。  
  
 如果要规矩这些冲突，必须派生类中重写 `PostNcDestroy` 方法。  若要添加自动清理到类中，然后实现 `delete this`调用基类。  若要从类移除自动清理，请调用 `CWnd::PostNcDestroy` 而不直接是直接基类的 `PostNcDestroy` 方法。  
  
 最常见更改自动清理行为是创建在堆可以赋予的无模式对话框。  
  
## 当调用 Delete 时：  
 建议您调用 `DestroyWindow`，销毁窗口对象方法或 C\+\+ 全局 `DestroyWindow` API。  
  
 请勿调用全局 `DestroyWindow` API 销毁 MDI 子窗口。  而应使用 `CWnd::DestroyWindow`。  
  
 对于 C\+\+ 不执行自动清理的窗口对象，使用 `delete` 运算符会导致内存泄漏，如果尝试调用 `CWnd::~CWnd` 析构函数时为 `DestroyWindow`，如果 VTBL 不正确指向派生类。  因为系统找不到相应销毁方法调用，则会发生这种情况。  使用 `delete` 而不是 `DestroyWindow` 来避免这些问题。  由于这是一细微的错误，请编译调试模式将生成以下警告您是危险的。  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
   OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 对于 C\+\+ 来自动清理的窗口对象，您必须调用 `DestroyWindow`。  如果直接使用 `delete` 运算符，MFC 诊断内存分配器将通知您释放内存两次。  两个 byte 是第显式调用和间接调用 `PostNcDestroy`中自动清理实现的 `delete this`。  
  
 在调用非自动清理对象的 `DestroyWindow` 之后，C\+\+ 对象，`m_hWnd`，但为 NULL。  在调用自动清理对象的 `DestroyWindow` 之后，将转到 C\+\+ 对象，释放由 `PostNcDestroy`C\+\+ 实现的自动清理的删除运算符。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)