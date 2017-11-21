---
title: "关于选择 ATL 和 MFC 建议 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d912c6cd997c23b9623d20a104327fb6e4701494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>ATL 和 MFC 之间进行选择的建议
在开发时组件和应用程序，你可以选择两种方法之间-ATL 和 MFC （Microsoft 基础类库）。  
  
## <a name="using-atl"></a>使用 ATL  
 ATL 是一种在同时在 c + + 中创建 COM 组件和维护内存占用较小的快速而方便的方法。 使用 ATL 创建的控件，如果你不需要所有 MFC 自动提供的内置功能。  
  
## <a name="using-mfc"></a>使用 MFC  
 MFC 允许你创建完整的应用程序、 ActiveX 控件和活动文档。 如果你已创建了一个控件使用 MFC，你可能想要在 MFC 中继续开发。 创建新控件时，请考虑使用 ATL，如果你不需要的所有 MFC 的内置功能。  
  
## <a name="using-atl-in-an-mfc-project"></a>在 MFC 项目中使用 ATL  
 你可以添加对现有 MFC 项目中使用 ATL，通过运行向导支持。 有关详细信息，请参阅[向 MFC 项目添加 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 简介](../atl/introduction-to-atl.md)

