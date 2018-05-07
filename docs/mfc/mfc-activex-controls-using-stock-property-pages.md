---
title: MFC ActiveX 控件： 使用常用属性页 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e8d54f87e4e018a004bbab503664fa1788f36c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控件：使用常用属性页
本文讨论了常用属性页可用于 ActiveX 控件和如何使用它们。  
  
 在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：  
  
-   [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC 提供三个常用属性页，以供使用 ActiveX 控件： **CLSID_CColorPropPage**， **CLSID_CFontPropPage**，和**CLSID_CPicturePropPage**。 这些页面分别显示用于常用颜色、 字体和图片属性的用户界面。  
  
 若要将这些属性页合并到一个控件，请向初始化的属性页 Id 的控件的数组的代码添加及其 Id。 在下面的示例中，此代码位于控件实现文件 (。CPP) 中，初始化数组以包含所有三个常用属性页和的默认属性页 (名为`CMyPropPage`在此示例中):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 请注意的计数属性页面，在`BEGIN_PROPPAGEIDS`宏，为 4。 这表示 ActiveX 控件支持的属性页中的数。  
  
 这些修改之后，重新生成项目。 控件现在具有字体、 图片和颜色属性的属性页。  
  
> [!NOTE]
>  如果无法访问控件常用属性页，则可能是因为 MFC DLL (MFCxx.DLL) 尚未正确注册与当前操作系统。 这通常导致在不同于当前正在运行的操作系统安装 Visual c + +。  
  
> [!TIP]
>  如果你的常用属性页不可见 （请参阅上一注释），通过对该 DLL 从命令行中使用的完整路径名称运行 RegSvr32.exe 注册 DLL。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)

