---
title: 关于选择 ATL 和 MFC 建议 |Microsoft 文档
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
ms.openlocfilehash: 116f2066b98951aa2a470021f5527542ac8cbe46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>ATL 和 MFC 之间进行选择的建议
在开发时组件和应用程序，你可以选择两种方法之间-ATL 和 MFC （Microsoft 基础类库）。  
  
## <a name="using-atl"></a>使用 ATL  
 ATL 是一种在同时在 c + + 中创建 COM 组件和维护内存占用较小的快速而方便的方法。 使用 ATL 创建的控件，如果你不需要所有 MFC 自动提供的内置功能。  
  
## <a name="using-mfc"></a>使用 MFC  
 MFC 允许你创建完整的应用程序、 ActiveX 控件和活动文档。 如果你已创建了一个控件使用 MFC，你可能想要在 MFC 中继续开发。 创建新控件时，请考虑使用 ATL，如果你不需要的所有 MFC 的内置功能。  
  
## <a name="using-atl-in-an-mfc-project"></a>在 MFC 项目中使用 ATL  
 你可以添加对现有 MFC 项目中使用 ATL，通过运行向导支持。 有关详细信息，请参阅[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
## <a name="see-also"></a>请参阅  
 [ATL 简介](../atl/introduction-to-atl.md)

