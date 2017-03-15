---
title: "TN030：自定义打印和打印预览 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.print"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义打印和打印预览"
  - "打印预览, 自定义"
  - "打印 [MFC], 视图"
  - "打印视图"
  - "TN030"
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN030：自定义打印和打印预览
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明自定义打印和打印预览过程介绍在 `CView` 的回调例程和回调例程的目的和 **CPreviewView**的成员函数。  
  
## 问题  
 MFC 为大多数打印和打印预览需要提供了完整的解决方案。  在许多情况下，需要一个额外代码可能的视图和打印预览。  但是，在需要大量成就在部分开发人员的情况下打印优化，并且，某些应用程序确实需要将特定用户界面元素到打印预览模式。  
  
## 高效的打印  
 当通过标准方法的 MFC 应用程序打印，窗口处理任何图形设备接口 \(GDI\) 输出对内存图元文件。  调用 `EndPage` 时，一次播放 Windows 元文件需要打印机打印一页上的每个物理带的。  在呈现期间，GDI 频繁查询中止过程确定是否应继续。  通常中止过程允许消息处理，以便使用打印对话框，用户能中止打印作业。  
  
 遗憾的是，这会降低晒印方法。  如果应用程序快速打印的绑定使用的标准方法，可以比实现，则必须实现手动分级。  
  
## 打印分级  
 手动耦合，必须关于实现打印循环调用每页这样 `OnPrint` 的多次 \(一次每个带区\)。  打印循环在 viewprnt.cpp **OnFilePrint** 函数的实现。  在 `CView`派生类，则重载此函数，以便处理的打印"命令消息映射项调用打印功能。  复制并 **OnFilePrint** 例程更改打印循环实现分级。  您可能还需要将分级矩形到打印函数，以便优化基于打印的页面节的绘图。  
  
 接下来，必须频繁调用 `QueryAbort`，则绘制带时。  否则，中止过程调用不会接收，用户无法取消打印作业。  
  
## 打印预览：有用户界面的电子音乐纸张  
 打印预览，实际上，显示的尝试将转换为打印机的模拟。  默认情况下，主窗口的工作区用于完整地显示两页在窗口中。  用户可以放大的页面区域更详细地查看它。  如果发生其他支持，用户可能更不允许编辑在预览模式的文档。  
  
## 自定义打印预览  
 此注释只修改处理的打印预览一个特性：添加 UI 为预览模式。  其他修改是可能的，但此更改，是超出此讨论的大小。  
  
## 添加 UI 为预览模式  
  
1.  从 **CPreviewView**派生一视图类。  
  
2.  添加您所需 UI 的特性的命令处理程序。  
  
3.  如果添加可视方面为显示，请重写 `OnDraw` 并在调用 **CPreviewView::OnDraw.**之后执行绘制  
  
## OnFilePrintPreview  
 这是打印预览的命令处理程序。  它的默认实现为：  
  
```  
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
        delete pState;      // preview failed to initialize,   
                    // delete State now  
    }  
}  
```  
  
 **DoPrintPreview** 会将隐藏应用程序主窗格。  控件条，如状态栏，可以通过指定它们在 pState\-\>**dwStates** 成员 \(这是位掩码，各个控件条位由 **AFX\_CONTROLBAR\_MASK**\(AFX\_IDW\_MYBAR\) 定义。  窗口 pState\-\>**nIDMainPane** 是自动隐藏和 reshown 的窗口。  **DoPrintPreview** 将创建一个预览标准 UI 的按钮栏   如果特定的窗口处理需要的，如隐藏或显示其他窗口，应执行，在调用 **DoPrintPreview** 之前。  
  
 默认情况下，当完成打印预览控件条时，它返回到其原始状态并且主窗格为可见。  如果特定的处理是必需的，它在 **EndPrintPreview.**重写应完成如果 **DoPrintPreview** 失败，也提供特殊处理。  
  
 DoPrintPreview 调用的：  
  
-   对话框模板的资源 ID 预览工具栏的。  
  
-   对执行打印预览中打印视图的指针。  
  
-   预览视图类的运行时类。  这 将在 DoPrintPreview中动态创建。  
  
-   CPrintPreviewState 指针。  请注意框架上*不*可以创建 CPrintPreviewState 结构 \(或派生的结构，则应用程序需要更多的状态保留\)。  DoPrintPreview 非模式，并且此结构必须生存直到 EndPrintPreview 调用。  
  
    > [!NOTE]
    >  如果单独视图或视图类支持打印的需要，应传递对该对象的指针作为第二个参数。  
  
## EndPrintPreview  
 这称为以打印预览模式。  移动到上次在打印预览中显示的文档页通常是需要的。  **EndPrintPreview** 是应用程序的可能性执行此操作。  pInfo\-\>`m_nCurPage` 成员是上显示的页 \(最左边，如果两页中显示出来\)，并且指针是页面上用户感兴趣的提示。  因为应用程序的视图结构未知到框架，则必须提供代码以移动到选择的点。  
  
 应在调用 **CView::EndPrintPreview**前运行大多数操作。  此调用 Undo **DoPrintPreview** 的效果和删除 pView、pDC 和 pInfo。  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC, pInfo, point, pView);  
```  
  
## CWinApp::OnFilePrintSetup  
 必须为打印设置菜单项映射此操作。  在大多数情况下，不必重写实现的。  
  
## 页命名法  
 另一议题是页码和排序。  对于简单的字处理器类型应用程序，这是一个直接的问题。  大多数系统将认为方法，打印预览每个打印的页对应的文档中的一页。  
  
 在尝试提供通用解决方案，需要考虑几个问题。  假设一种计算机辅助设计系统。  用户具有包含多 E 范围表的绘图。  E 在大小 \(或小，缩放\) 绘图仪上，页码在简单的情况。  但在激光打印机上，打印每页16 A\-大小的单子，打印预览如何考虑一个“内容页”?  
  
 作为介绍性段落状态，如打印机打印预览操作。  因此，用户将看到从选择的特殊的打印机的输出。  将由视图来确定每个页面上打印的图像。  
  
 在 `CPrintInfo` 配置的页面描述字符串的方法向用户显示页码，则可表示为每页一个数字 \(“Page 1 "或“1\-2 页”\)。此字符串用于**CPreviewView::OnDisplayPageNumber**的默认实现。  如果不同的显示是必需的，一个可能重写此虚函数提供，Sheet1 部分，例如，“A，B”。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)