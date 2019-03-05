---
title: MFC ActiveX 控件：使用常用属性页
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
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
ms.openlocfilehash: b73a027422cfe9cbf03afece400c1b513cace151
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304699"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控件：使用常用属性页

本文介绍可用于 ActiveX 控件以及如何使用这些常用属性页。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

使用 ActiveX 控件中的属性页面的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：添加另一个自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC 还提供了三个常用属性页，可用于 ActiveX 控件： `CLSID_CColorPropPage`， `CLSID_CFontPropPage`，和`CLSID_CPicturePropPage`。 这些页面分别显示用于常用颜色、 字体和图片属性的用户界面。

若要将这些属性页合并到一个控件，将其 Id 添加到初始化的属性页 Id 的控件的数组的代码。 在以下示例中，此代码位于控件实现文件 (。CPP)，初始化该数组以包含所有三个常用属性页和默认属性页 (名为`CMyPropPage`在此示例中):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

请注意属性页中，在 BEGIN_PROPPAGEIDS 宏的计数为 4。 这表示 ActiveX 控件支持的属性页面的数量。

在进行这些修改后，重新生成项目。 您的控件现在具有字体、 图片和颜色属性的属性页。

> [!NOTE]
>  如果不能访问控件常用属性页，则可能是因为 MFC DLL (MFCxx.DLL) 尚未正确注册与当前操作系统。 这通常会在不同于当前正在运行的操作系统安装 Visual c + +。

> [!TIP]
>  如果常用属性页是不可见 （请参阅上一个便笺），通过运行 RegSvr32.exe 命令行中使用的完整路径名称从 dll 注册该 DLL。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)
