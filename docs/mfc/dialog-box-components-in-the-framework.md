---
title: 框架中的对话框组件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: b3290107337f60854e6abbd2f744aaa38af0b741
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616926"
---
# <a name="dialog-box-components-in-the-framework"></a>框架中的对话框组件

在 MFC 框架中，对话框有两个组件：

- 对话框模板资源，用来指定对话框的控件及其位置。

   对话框资源存储 Windows 从中创建并显示对话框窗口的对话框模板。 该模板指定对话框的特征，包括其大小、位置、样式以及对话框的控件的类型和位置。 您通常会使用作为资源存储的对话框模板，但您也可以在内存中创建自己的模板。

- 一个从[CDialog](reference/cdialog-class.md)派生的对话框类，提供用于管理对话框的编程接口。

   对话框是一个窗口，它在可见时将附加到 Windows 窗口。 创建对话框窗口后，对话框模板资源将用作用于创建对话框的子窗口控件的模板。

## <a name="see-also"></a>另请参阅

[对话框](dialog-boxes.md)<br/>
[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
