---
title: 创建活动文档容器应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616342"
---
# <a name="creating-an-active-document-container-application"></a>创建活动文档容器应用程序

最简单、最受推崇的活动文档容器应用程序的创建方式为使用 MFC 应用程序向导创建 MFC EXE 容器应用程序，然后将应用程序修改为支持活动文档包容。

#### <a name="to-create-an-active-document-container-application"></a>创建活动文档容器应用程序

1. 从 "**文件**" 菜单中，单击 "**新建**" 子菜单中的 "**项目**"。

1. 在左侧窗格中，单击 " **Visual C++** 项目类型"。

1. 从右窗格中选择 " **MFC 应用程序**"。

1. 将项目命名为*myproj.csproj*，然后单击 **"确定"**。

1. 选择 "**复合文档支持**" 页。

1. 选择**容器**或**容器/完全服务器**选项。

1. 选中 "**活动文档容器**" 复选框。

1. 单击“完成”。

1. 当 MFC 应用程序向导完成应用程序生成时，使用解决方案资源管理器打开下列文件：

   - *MyProjview.cpp*

1. 在*MyProjview*中进行以下更改：

   - 在 `CMyProjView::OnPreparePrinting` 中，将函数内容替换为下列代码：

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` 将提供打印支持。 此代码将替换 `DoPreparePrinting`，其是默认打印准备。

   活动文档包容将提供改进的打印方案：

   - 您可以先通过其接口调用活动文档 `IPrint` ，并告诉它打印自身。 这不同于以前的 OLE 包容，其中容器必须将包含项的图像呈现到 printer `CDC` 对象上。

   - 如果失败，请通知包含的项通过其 `IOleCommandTarget` 接口打印

   - 如果失败，自行呈现项目。

   如之前的代码所实现的一样，`COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting` 将处理此改进的打印方案。

1. 添加您自己的任何实现并生成应用程序。

## <a name="see-also"></a>另请参阅

[活动文档包容](active-document-containment.md)
