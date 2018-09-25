---
title: TN030： 自定义打印和打印预览 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.print
dev_langs:
- C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8331bbde9cf749d3b86b8970543d7a3b46be90fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381135"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030：自定义打印和打印预览

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍的自定义打印和打印预览过程并介绍在中使用的回调例程的目的`CView`回调例程和的成员函数和`CPreviewView`。

## <a name="the-problem"></a>问题

MFC 提供了一个完整的解决方案，大多数打印和打印预览需求。 在大多数情况下，一些额外的代码时需要有一个可以进行打印或预览的视图。 但是，有方法来优化打印需要大量工作，开发人员来说，并且某些应用程序需要将特定的用户界面元素添加到打印预览模式。

## <a name="efficient-printing"></a>有效地进行打印

当 MFC 应用程序打印使用标准的方法时，Windows 将定向到内存中图元文件的所有图形设备接口 (GDI) 输出调用。 当`EndPage`是调用，Windows 播放一次为每个打印机要求通过打印一页的物理带区图元文件。 在此呈现期间 GDI 经常查询中止过程来确定是否应继续。 通常中止过程，以便用户可能会终止使用打印对话框的打印作业处理的消息。

遗憾的是，这可能会降低打印进程。 如果在应用程序中的打印必须是不是可以使用标准的技术来实现更快，则必须实现手动条带。

## <a name="print-banding"></a>打印条带

若要手动外，您必须重新实现打印循环，以便`OnPrint`多次调用每页 （一次每个外）。 在中实现打印循环`OnFilePrint`viewprnt.cpp 中的函数。 在你`CView`-派生的类，此函数重载，以便处理打印命令的消息映射项调用打印功能。 复制`OnFilePrint`例程和更改打印循环来实现条带。 您将可能还想要将具有带区矩形传递到打印功能，以便可以优化绘图基于正在打印页的部分。

其次，必须频繁地调用`QueryAbort`绘制带区时。 否则为将不会调用中止过程和用户将无法取消打印作业。

## <a name="print-preview-electronic-paper-with-user-interface"></a>打印预览： 在电子纸张的用户界面

打印预览中，从本质上讲，尝试打开到打印机的模拟显示。 默认情况下，主窗口的客户端区域用于显示完全在窗口中的一个或两个页面。 用户可放大页面以查看更详细地区域。 与其他支持，用户甚至可能允许以预览模式中编辑该文档。

## <a name="customizing-print-preview"></a>自定义打印预览

修改打印预览的一个方面只处理此说明： 添加用户界面，以预览模式。 其他修改是可能的但此类更改超出了本文的讨论范围。

## <a name="to-add-ui-to-the-preview-mode"></a>若要将 UI 添加到预览模式

1. 派生视图类从`CPreviewView`。

2. 添加所需的 UI 方面的命令处理程序。

3. 如果要添加到显示的可视方面，重写`OnDraw`并执行后调用在绘图`CPreviewView::OnDraw`。

## <a name="onfileprintpreview"></a>OnFilePrintPreview

这是为打印预览命令处理程序。 其默认实现是：

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` 将隐藏的应用程序的主窗格。 控件条，如状态栏中，可保留在 pState 中指定->*dwStates*成员 （这是一个位掩码和 bits 通过 AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR) 定义单个控件条）。 -> 窗口 pState*nIDMainPane*是将自动隐藏和 reshown 的窗口。 `DoPrintPreview` 然后将标准预览版用户界面创建一个菜单栏。 如果需要特殊的窗口处理，如对隐藏或显示其他窗口，应完成之前的`DoPrintPreview`调用。

默认情况下，当打印预览完成后，它返回控件条到其原始状态和主窗格中可见。 如果需要特殊处理，才应执行的重写中`EndPrintPreview`。 如果`DoPrintPreview`失败，则还提供特殊处理。

使用调用 DoPrintPreview:

- 预览工具栏上的对话框模板资源 ID。

- 指向要执行打印为打印预览的视图的指针。

- 预览视图类的运行时类。 这将 DoPrintPreview 中动态创建。

- CPrintPreviewState 指针中。 请注意 CPrintPreviewState 结构 （或如果在应用程序需要保留的详细状态的派生的结构） 必须*不*在框架上创建。 DoPrintPreview 是无模式，此结构必须能够调用 EndPrintPreview 为止。

  > [!NOTE]
  > 如果打印支持需要单独的视图或视图类，应作为第二个参数传递给该对象的指针。

## <a name="endprintpreview"></a>EndPrintPreview

这称为终止打印预览模式。 通常是需要将移动到上一次显示在打印预览的文档中的页。 `EndPrintPreview` 是执行此操作的应用程序的机会。 -> PInfo*m_nCurPage*成员是上次显示 （如果显示两个页面的左侧，） 的页面且指针位于提示以指明在其中的页上用户感。 由于应用程序的视图的结构是未知的框架，因此必须提供代码以移动到所选点。

你应执行大多数操作之前调用`CView::EndPrintPreview`。 此调用都颠倒的效果`DoPrintPreview`并删除 pView、 pDC 和 pInfo。

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

这必须映射为打印设置菜单项。 在大多数情况下，不需要重写实现。

## <a name="page-nomenclature"></a>页面命名法

另一个问题是页编号和顺序。 对于简单的字处理器类型应用程序，这是一个简单的问题。 大多数打印预览系统假定每个打印的页面对应于文档中的一页。

在尝试提供通用的解决方案，有一些事项需要注意。 设想有一个 CAD 系统。 用户具有涵盖多个电子大小工作表中的图形。 E 大小 （或更小，缩放） 页编号如下所示的简单情况下是合适的绘图仪。 但激光打印机，打印每张纸打印，16 一个大小的页上什么才会打印预览认为"页"

介绍性段落指出，实际上打印机起打印预览。 因此，用户将看到从选择特定打印机会出现什么内容。 它是由视图来确定每个页面上打印的映像。

中的页说明字符串`CPrintInfo`结构提供了一种向用户显示的页码，如果它可以表示为每页的一个数字 (如"第 1 页"或"页面 1-2")。 默认实现将使用此字符串`CPreviewView::OnDisplayPageNumber`。 如果需要不同的显示，则一个可能会覆盖此虚拟函数，可提供，例如，"Sheet1，部分 A，B"。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
