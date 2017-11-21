---
title: "ATL 控件： 常规支持类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.controls
dev_langs: C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5d969481874762c5eefeb805d954ffad6114033e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="controls-general-support-classes"></a>控件： 常规支持类
下面的类为 ATL 控件提供常规支持：  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md)包含至关重要 ATL 控件的帮助器函数和数据成员。  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md)提供所需控件的方法。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)的某个控件一起提供的主体的方法，通过该容器进行通信。 管理激活和停用的就地控件。  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md)将合并到一个调用以帮助避免的延迟加载控件时的容器的初始化。  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md)提供否则为不活动的控件的最小鼠标交互。  
  
## <a name="sample-program"></a>示例程序  
 [ATLFire](../visual-cpp-samples.md)  
  
## <a name="related-articles"></a>相关文章  
 [ATL 教程](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../atl/atl-class-overview.md)

