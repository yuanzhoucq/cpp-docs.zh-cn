---
title: ActiveX 控件容器：手动启用 ActiveX 控件包含
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625105"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控件容器：手动启用 ActiveX 控件包含

如果您在使用 MFC 应用程序向导生成应用程序时未启用 ActiveX 控件支持，则将必须手动添加此支持。 本文介绍了手动将 ActiveX 控件包含添加到现有 OLE 容器应用程序的过程。 如果事先知道您需要 OLE 容器中的 ActiveX 控件支持，请参阅[创建 MFC ActiveX 控件容器一](reference/creating-an-mfc-activex-control-container.md)文。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

> [!NOTE]
> 本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

若要支持 ActiveX 控件，则你必须向这两个项目的文件添加一行代码。

- 修改主对话框的 `InitInstance` 函数（在容器中找到。CPP），MFC 应用程序向导对[AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)进行调用，如以下示例中所示：

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 向项目的 STDAFX.H 头文件添加以下代码：

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

完成这些步骤后，通过单击 "**生成**" 菜单上的 "**生成**" 来重新生成项目。

## <a name="see-also"></a>另请参阅

[ActiveX 控件容器](activex-control-containers.md)
