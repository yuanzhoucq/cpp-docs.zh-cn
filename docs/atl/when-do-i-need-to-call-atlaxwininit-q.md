---
title: "何时需要调用 AtlAxWinInit？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AtlAxWinInit
dev_langs: C++
helpviewer_keywords: AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ec7d8d15b8219071b593368ed539d92ff3c9032
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>何时需要调用 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)注册**"AtlAxWin80"**窗口类 （加上一些自定义窗口消息），以便在尝试将宿主窗口创建前，必须调用此函数。 但是，始终不需要显式调用此函数，自承载 Api （和使用它们的类） 通常为您调用此函数。 没有任何影响不止一次调用此函数。 .  
  
## <a name="see-also"></a>另请参阅  
 何时需要调用 AtlAxWinTerm     
 [控件包含常见问题](../atl/atl-control-containment-faq.md)
