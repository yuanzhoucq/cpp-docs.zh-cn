---
title: "TN030： 自定义打印和打印预览 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa11c30fb41630a5b293698fe3e69a80509f3f2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030：自定义打印和打印预览
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍自定义打印和打印预览的过程和说明中使用的回调例程的用途`CView`回调例程和的成员函数**CPreviewView**。  
  
## <a name="the-problem"></a>问题  
 MFC 提供了一个完整的解决方案，大多数打印和打印预览需求。 在大多数情况下，很少的其他代码都需要有一个视图，可以打印并预览。 但是，有方法可以优化打印需要大量精力，开发人员，并且某些应用程序需要将特定的用户界面元素添加到打印预览模式。  
  
## <a name="efficient-printing"></a>有效地进行打印  
 MFC 应用程序将打印使用标准的方法，当 Windows 所有图形设备接口 (GDI) 输出将调用定向到内存中图元文件。 当`EndPage`是调用，Windows 在播放一次为每个打印机要求要打印一页的物理带区图元文件。 此呈现期间 GDI 经常查询该中止的过程，以确定是否应继续。 通常中止过程允许消息处理，以便用户可能中止打印作业使用打印对话框。  
  
 遗憾的是，这样会降低打印过程。 如果你的应用程序中的打印必须不是可以使用标准的技术来实现更快，则必须实现手动条带。  
  
## <a name="print-banding"></a>打印条带  
 要手动对带外，你必须重新实现打印循环以便`OnPrint`每页 （一次每个带区） 多次调用。 在中实现打印循环**OnFilePrint** viewprnt.cpp 中的函数。 在你`CView`-派生类，以便用于处理打印命令消息映射条目调用打印函数重载此函数。 复制**OnFilePrint**例程和更改打印循环实现条带。 你将可能还想要将具有带区的矩形传递给打印功能，以便你可以优化绘制基于打印页的部分。  
  
 其次，必须频繁调用`QueryAbort`时绘制带区。 否则为将不会调用中止过程和用户将无法取消该打印作业。  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>打印预览： 电子纸与用户界面  
 打印预览，实质上，尝试打开到模拟的打印机的显示。 默认情况下，主窗口的工作区用于显示完全在窗口内的一个或两个页。 用户就能够放大页后，可以在更多详细信息中看到它的区域。 额外支持，用户即使可能允许编辑预览模式中的文档。  
  
## <a name="customizing-print-preview"></a>自定义打印预览  
 与的修改打印预览的一个方面只涉及本说明： 添加用户界面，以预览模式。 其他修改是可能的但此类更改已超出本文的讨论范围。  
  
## <a name="to-add-ui-to-the-preview-mode"></a>若要将用户界面添加到预览模式  
  
1.  派生视图类从**CPreviewView**。  
  
2.  添加 UI 方面所需的命令处理程序。  
  
3.  如果你要添加到显示的可视方面，重写`OnDraw`和执行后调用你绘制**CPreviewView::OnDraw。**  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 这是为打印预览命令处理程序。 其默认实现是：  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 **DoPrintPreview**将隐藏应用程序的主窗格。 控件条，如状态栏中，可以保留通过指定中 pState->**dwStates**成员 (这是一个位掩码，并由定义的位以单个控件条**AFX_CONTROLBAR_MASK**(AFX_IDW_MYBAR))。 窗口 pState->**nIDMainPane**是将自动隐藏和 reshown 的窗口。 **DoPrintPreview**然后将为标准的预览版 UI 创建一个菜单栏。 如果需要特殊的窗口处理，如隐藏或显示其他 windows，应完成之前需要**DoPrintPreview**调用。  
  
 默认情况下，如果打印预览完成后，则返回控件条到其原始状态和主窗格中可见。 如果需要特殊处理，则它应进行的重写中**EndPrintPreview。** 如果**DoPrintPreview**失败，还提供特殊处理。  
  
 使用调用 DoPrintPreview:  
  
-   预览工具栏的对话框模板资源 ID。  
  
-   指向要为打印预览中执行打印的视图的指针。  
  
-   预览视图类的运行时类。 这将在 DoPrintPreview 中动态创建。  
  
-   CPrintPreviewState 指针。 请注意 CPrintPreviewState 结构 （或如果应用程序需要保留的详细状态的派生的结构） 必须*不*在帧上创建。 DoPrintPreview 是无模式，直到调用 EndPrintPreview 会必须保留此结构。  
  
    > [!NOTE]
    >  如果打印支持需要单独的视图或视图类，应作为第二个参数传递给该对象的指针。  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 这称为终止打印预览模式。 它通常是需要移动到上次在打印预览中显示的文档中的页。 **EndPrintPreview**是执行该操作的应用程序的机会。 PInfo->`m_nCurPage`成员是上次显示 （如果显示两个页面的左侧，） 页，并且指针是关于在页上关注用户是其中一个提示。 由于应用程序的视图的结构是未知的框架，你必须提供代码以移动到选定的点。  
  
 你应执行大多数操作之前调用**CView::EndPrintPreview**。 此调用反转的效果**DoPrintPreview**并删除 pView、 pDC 和 pInfo。  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 这必须打印设置菜单项映射。 在大多数情况下，不需要重写的实现。  
  
## <a name="page-nomenclature"></a>页命名法  
 另一个问题是页码和顺序。 对于简单的字处理器类型应用程序，这是一个简单的问题。 大多数打印预览系统假定每个打印的页的文档中的一个页面对应。  
  
 在尝试提供通用的解决方案，有一些事项需要注意。 设想有一个 CAD 系统。 用户具有涵盖多个 E 大小工作表中的图形。 E 大小 （或较小，缩放） 绘图仪，页码将如下所示的简单情况。 但在激光打印机，打印每个表，16 A 大小页上未打印预览考虑的内容"页"  
  
 正如所指出的介绍性段落，打印预览作用好似打印机。 因此，用户将看到什么将离开选择特定打印机。 负责视图以确定哪些图像打印每一页上。  
  
 中的页说明字符串`CPrintInfo`结构提供了一种向用户显示页码，如果它可以表示为每页的一个数字 (如所示"第 1 页"或"页 1-2")。 此字符串的默认实现使用**CPreviewView::OnDisplayPageNumber**。 如果需要不同的显示，则一个可能会覆盖此虚拟函数，可提供，例如，"Sheet1，部分 A，B"。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

