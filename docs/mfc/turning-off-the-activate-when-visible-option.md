---
title: 关闭激活时可见选项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cb585496e6acf1c0ad94a43500e6d9a4830a2ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381271"
---
# <a name="turning-off-the-activate-when-visible-option"></a>关闭“可见时激活”选项

控件有两种基本状态： 活动和非活动。 传统上，控件是否有一个窗口来区分这些状态。 活动控件有窗口;不支持的非活动状态的控件。 无窗口激活的引入，这一区别不再是通用的但仍适用于许多控件。

与通常由 ActiveX 控件执行的初始化的其余工作相比，创建窗口是一个资源消耗很大的操作。 理想情况下，控件会推迟创建其窗口，直到非要执行此操作。

许多控件在其在容器中可见的整个时间不需要是活动的。 通常，控件可保持不活动状态，直到用户执行需要此控件变为活动状态的操作（例如，使用鼠标单击或按 Tab 键）。 若要使控件处于不活动状态，直到该容器需要激活它，请删除**OLEMISC_ACTIVATEWHENVISIBLE**从控件的各种标志的标志：

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

**OLEMISC_ACTIVATEWHENVISIBLE**如果您关闭，则将自动省略标志**可见时激活**选项[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX 页控件向导创建您的控件时。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

