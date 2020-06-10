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
ms.openlocfilehash: 18e482ca93166246df7569be9babff93d983dfd5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618063"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 控件：使用常用属性页

本文介绍 ActiveX 控件可用的常用属性页以及如何使用它们。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：添加另一自定义属性页](mfc-activex-controls-adding-another-custom-property-page.md)

MFC 提供了三种常用属性页，用于 ActiveX 控件： `CLSID_CColorPropPage` 、 `CLSID_CFontPropPage` 和 `CLSID_CPicturePropPage` 。 这些页面分别显示 stock 颜色、字体和图片属性的用户界面。

若要将这些属性页合并到控件中，请将其 Id 添加到初始化控件的属性页 Id 数组的代码。 在下面的示例中，此代码位于控件实现文件（。CPP），将数组初始化为包含所有三个常用属性页和默认属性页（ `CMyPropPage` 在本示例中命名为）：

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

请注意，BEGIN_PROPPAGEIDS 宏中的属性页计数为4。 这表示 ActiveX 控件支持的属性页的数目。

完成这些修改后，重新生成项目。 控件现在具有 "字体"、"图片" 和 "颜色" 属性的属性页。

> [!NOTE]
> 如果无法访问控制存货属性页，可能是因为 MFC DLL （Mfcxx.dll）未正确地注册到当前操作系统。 这通常是因为在操作系统下安装 Visual C++ 不同于当前正在运行的操作系统。

> [!TIP]
> 如果您的常用属性页不可见（请参阅上一条注释），请从命令行中使用 DLL 的完整路径名称运行 RegSvr32 来注册 DLL。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：添加常用属性](mfc-activex-controls-adding-stock-properties.md)
