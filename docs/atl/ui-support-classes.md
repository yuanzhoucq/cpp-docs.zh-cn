---
title: "用户界面支持类 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.ui
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4b708dec433c120ddd8a938eadb3577a1a6d0f8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ui-support-classes"></a>支持的 UI 类
下面的类提供常规的 UI 支持：  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md)的 Microsoft HTML 分析和呈现引擎的接口。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)的某个控件一起提供的主体的方法，通过该容器进行通信。 管理激活和停用的就地控件。  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)管理的现有控件重新激活。 启用无窗口控件可以接收消息，以及要参与拖放操作。  
  
-   [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md)帮助就地控件与其容器之间的通信。  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md)使控件以显示本身直接和以通知容器中显示的更改。 提供无闪烁的绘制、 非矩形的透明控件和命中测试的支持。  
  
## <a name="related-articles"></a>相关文章  
 [ATL 教程](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>请参阅  
 [类概述](../atl/atl-class-overview.md)

