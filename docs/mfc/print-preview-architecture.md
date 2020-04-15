---
title: 打印预览结构
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375950"
---
# <a name="print-preview-architecture"></a>打印预览结构

本文介绍 MFC 框架如何实现打印预览功能。 涵盖的主题包括：

- [打印预览过程](#_core_the_print_preview_process)

- [修改打印预览](#_core_modifying_print_preview)

由于不是直接在设备上绘制图像，应用程序必须使用屏幕模拟打印机，因此打印预览某种程度上不同于屏幕显示和打印。 为了适应这种情况，Microsoft 基础类库定义了派生自[CDC 类](../mfc/reference/cdc-class.md)的特殊（未记录）类，`CPreviewDC`称为 。 所有 `CDC` 对象包含两个设备上下文，但这两个上下文一般是相同的。 在对象`CPreviewDC`中，它们是不同的：第一个表示正在模拟的打印机，第二个表示实际显示输出的屏幕。

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>打印预览过程

当用户从"**文件**"菜单中选择"打印预览"命令时，框架将创建一`CPreviewDC`个对象。 每当应用程序执行为打印机设备上下文设置特征的操作时，应用程序也将对屏幕设备上下文执行类似的操作。 例如，如果应用程序选择一种打印字体，则框架将选择一种模拟打印机字体的屏幕显示字体。 每当应用程序将输出发送到打印机时，框架会将输出发送到屏幕。

打印预览在绘制文档页面的顺序上也不同于打印。 打印期间，框架将继续打印循环，直到呈现特定范围的页面。 打印预览期间，任何时候都是显示一或两页，然后应用程序等待；在用户响应前不再显示任何页面。 在打印预览期间，应用程序还必须响应WM_PAINT消息，就像在普通屏幕显示时一样。

调用预览模式时调用[CView：onPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)功能，就像打印作业开始时一样。 传递给该函数的[CPrintInfo 结构](../mfc/reference/cprintinfo-structure.md)包含多个成员，您可以设置其值以调整打印预览操作的某些特征。 例如，您可以将*m_nNumPreviewPages*成员设置为指定是要以单页还是两页模式预览文档。

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>修改打印预览

您可以通过很多特别简单的方式修改打印预览的行为和外观。 例如，除了别的之外，您可以：

- 使打印预览窗口显示滚动条，以便轻松访问文档的任何页。

- 使打印预览保留用户在文档中的位置，方式为在当前页开始其显示。

- 促使为打印预览和打印执行不同的初始化。

- 使打印预览用您自己的格式显示页码。

如果您知道文档的长度并使用适当的值调用 `SetMaxPage`，则框架可在预览模式以及打印期间使用此信息。 一旦框架知道文档的长度，它可提供带滚动条的预览窗口，允许用户在预览模式的文档中来回翻页。 如果您尚未设置文档长度，则框架无法放置滚动条来指示当前位置，因此框架不会添加滚动条。 在这种情况下，用户必须使用预览窗口控件条上的“下一页”和“上一页”按钮对文档翻页。

对于打印预览，您可能会发现将值分配给 m_nCurPage`CPrintInfo`*成员很有用*，即使您永远不会为普通打印分配该值。 在普通打印期间，此成员会将信息从框架传递到视图类。 这是框架告知视图应打印哪一页的方式。

相反，当开始打印预览模式时 *，m_nCurPage*成员以相反的方向传递信息：从视图到框架。 框架将使用此成员的值确定应先预览的页。 此成员的默认值为 1，因此将先显示文档的第一页。 您可重写 `OnPreparePrinting` 以将此成员设置为要在调用“打印预览”命令时查看的页的页码。 这样，当从普通显示模式切换到打印预览模式时，应用程序将保留用户的当前位置。

有时，您可能希望 `OnPreparePrinting` 执行不同的初始化，这取决于它是为打印作业还是为打印预览调用的。 您可以通过检查结构中*m_bPreview*成员变量来确定这一`CPrintInfo`点。 调用打印预览时，此成员设置为**TRUE。**

该`CPrintInfo`结构还包含名为*m_strPageDesc*的成员，该成员用于以单页和多页模式设置屏幕底部显示的字符串的格式。 默认情况下，这些字符串的形式是"页*n"* 和"页*n* - *m"，* 但可以从*m_strPageDesc*内部`OnPreparePrinting`修改m_strPageDesc并将字符串设置为更详细的东西。 有关详细信息，请参阅*MFC 参考*中的[CPrintInfo 结构](../mfc/reference/cprintinfo-structure.md)。

## <a name="see-also"></a>另请参阅

[打印和打印预览](../mfc/printing-and-print-preview.md)<br/>
[打印](../mfc/printing.md)<br/>
[CView 类](../mfc/reference/cview-class.md)<br/>
[CDC 类](../mfc/reference/cdc-class.md)
