---
title: 关于选择 ATL 和 MFC 的建议
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: b3c01a54c1250ae97d5377cb0b1ff49a17c3f7c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468245"
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

