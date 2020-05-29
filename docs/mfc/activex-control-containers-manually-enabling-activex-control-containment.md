---
title: ActiveX 控件容器：手动启用 ActiveX 控件包含
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322065"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控件容器：手动启用 ActiveX 控件包含

如果您在使用 MFC 应用程序向导生成应用程序时未启用 ActiveX 控件支持，则将必须手动添加此支持。 本文介绍了手动将 ActiveX 控件包含添加到现有 OLE 容器应用程序的过程。 如果您事先知道在 OLE 容器中需要 ActiveX 控制支持，请参阅创建[MFC ActiveX 控制容器](../mfc/reference/creating-an-mfc-activex-control-container.md)的文章。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

> [!NOTE]
> 本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

若要支持 ActiveX 控件，则你必须向这两个项目的文件添加一行代码。

- 修改主对话框的功能`InitInstance`（见于"容器"中）。CPP） 由 MFC 应用程序向导调用[AfxEnableControl 容器](reference/ole-initialization.md#afxenablecontrolcontainer)，如以下示例所示：

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 向项目的 STDAFX.H 头文件添加以下代码：

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

完成这些步骤后，单击"**生成**"菜单上的 **"生成**"来重建项目。

## <a name="see-also"></a>另请参阅

[ActiveX 控制容器](../mfc/activex-control-containers.md)
