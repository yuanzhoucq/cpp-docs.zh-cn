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
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358200"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控件：使用常用属性页

本文讨论 ActiveX 控件可用的股票属性页以及如何使用它们。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC 提供了三个用于 ActiveX 控件的库存`CLSID_CColorPropPage`属性`CLSID_CFontPropPage`页：`CLSID_CPicturePropPage`和 。 这些页面分别显示股票颜色、字体和图片属性的用户界面。

要将这些属性页合并到控件中，请将其 ID 添加到初始化控件的属性页 ID 数组的代码中。 在下面的示例中，此代码位于控件实现文件中 （。CPP），初始化数组以包含所有三个股票属性页和默认属性页（在此示例中命名`CMyPropPage`）：

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

请注意，BEGIN_PROPPAGEIDS宏中的属性页的计数为 4。 这表示 ActiveX 控件支持的属性页数。

进行这些修改后，重新生成项目。 控件现在具有字体、图片和颜色属性的属性页。

> [!NOTE]
> 如果无法访问控件库存属性页，可能是因为 MFC DLL （MFCxx.DLL） 尚未与当前操作系统正确注册。 这通常是由于在不同于当前运行的操作系统下安装 Visual C++。

> [!TIP]
> 如果股票属性页不可见（请参阅上一条注释），请从具有 DLL 完整路径名称的命令行中运行 RegSvr32.exe 来注册 DLL。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)
