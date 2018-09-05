---
title: 关于选择 ATL 和 MFC 建议 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9bbf30c728b6562da0c56c25b177697f0882a5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762120"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>关于选择 ATL 和 MFC 的建议

在开发组件和应用程序时，你可以选择两种方法之间，ATL 和 MFC （Microsoft 基础类库）。

## <a name="using-atl"></a>使用 ATL

ATL 是快速、 简单的方法，以在 c + + 中创建 COM 组件并维护内存占用较小。 使用 ATL 创建控件，如果你不需要所有 MFC 自动提供的内置功能。

## <a name="using-mfc"></a>使用 MFC

MFC 允许您创建完整的应用程序、 ActiveX 控件和活动文档。 如果你已创建了一个控件使用 MFC，可能想要在 MFC 中继续进行开发。 当创建新的控件，请考虑使用 ATL，如果你不需要的所有 MFC 的内置功能。

## <a name="using-atl-in-an-mfc-project"></a>在 MFC 项目中使用 ATL

可以添加对通过运行向导在现有 MFC 项目中使用 ATL 的支持。 有关详细信息，请参阅[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

## <a name="see-also"></a>请参阅

[ATL 简介](../atl/introduction-to-atl.md)

