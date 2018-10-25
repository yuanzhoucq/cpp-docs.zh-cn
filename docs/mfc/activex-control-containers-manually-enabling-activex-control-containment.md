---
title: ActiveX 控件容器： 手动启用 ActiveX 控件包含 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f684bbb287213ad0cbe6d490c1bef869f5ffc9db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077772"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 控件容器：手动启用 ActiveX 控件包含

如果您在使用 MFC 应用程序向导生成应用程序时未启用 ActiveX 控件支持，则将必须手动添加此支持。 本文介绍了手动将 ActiveX 控件包含添加到现有 OLE 容器应用程序的过程。 如果您事先知道您的 OLE 容器中需要 ActiveX 控件支持，请参阅文章[创建 MFC ActiveX 控件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

> [!NOTE]
>  本文使用一个名为 Container、基于对话框的 ActiveX 控件容器项目和一个名为 Circ 的嵌入控件分别作为过程和代码中的示例。

若要支持 ActiveX 控件，则你必须向这两个项目的文件添加一行代码。

- 修改您的主对话框`InitInstance`函数 （在容器中找到。CPP) 调用 MFC 应用程序向导[AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)，如下面的示例：

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 向项目的 STDAFX.H 头文件添加以下代码：

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

完成这些步骤后，重新生成项目通过单击**构建**上**生成**菜单。

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)

