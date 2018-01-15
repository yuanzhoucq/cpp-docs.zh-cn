---
title: "WINDOWPLACEMENT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WINDOWPLACEMENT
dev_langs: C++
helpviewer_keywords: WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e73065cdf20d68b1da4ba77d1ad555e2bf95e937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT 结构
`WINDOWPLACEMENT`结构包含一个窗口的布局信息在屏幕上**。**  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
    UINT length;  
    UINT flags;  
    UINT showCmd;  
    POINT ptMinPosition;  
    POINT ptMaxPosition;  
    RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### <a name="parameters"></a>参数  
 *length*  
 指定的长度以字节为单位，结构的**。**  
  
 `flags`  
 指定可控制的最小化的窗口以及窗口还原所依据的方法的位置的标志。 此成员可以是一个或两个以下的标志：  
  
- **WPF_SETMINPOSITION**指定可以指定 x 和 y-位置的最小化窗口**。** 此标志必须指定坐标在中设置**ptMinPosition**成员。  
  
- **WPF_RESTORETOMAXIMIZED**指定，还原窗口将最大化，无论是否它被最大化之前被最小化。 此设置为有效仅还原窗口的下一次。 它不会更改默认还原行为。 此标志是仅当**SW_SHOWMINIMIZED**为指定值**showCmd**成员。  
  
 *showCmd*  
 指定窗口的当前显示的状态。 此成员可以是以下值之一：  
  
- **SW_HIDE**隐藏窗口，并将激活传递到另一个窗口。  
  
- **SW_MINIMIZE**最大程度减少指定的窗口和激活系统的列表中的顶级窗口。  
  
- **SW_RESTORE**激活并显示一个窗口。 如果对窗口进行最小化或最大化，Windows 将其还原到其原始大小和位置 (与相同**SW_SHOWNORMAL**)。  
  
- **SW_SHOW**激活窗口，并将其显示在其当前大小和位置。  
  
- **SW_SHOWMAXIMIZED**激活窗口，并将其显示为最大化窗口。  
  
- **SW_SHOWMINIMIZED**激活窗口，并将其显示为一个图标。  
  
- **SW_SHOWMINNOACTIVE**为图标会显示一个窗口。 当前处于活动状态窗口保持活动状态。  
  
- **SW_SHOWNA**在其当前状态会显示一个窗口。 当前处于活动状态窗口保持活动状态。  
  
- **SW_SHOWNOACTIVATE**显示一个窗口中的最新的大小和位置。 当前处于活动状态窗口保持活动状态。  
  
- **SW_SHOWNORMAL**激活并显示一个窗口。 如果对窗口进行最小化或最大化，Windows 将其还原到其原始大小和位置 (与相同**SW_RESTORE**)。  
  
 *ptMinPosition*  
 窗口最小化时，请指定窗口的左上角的位置。  
  
 `ptMaxPosition`  
 最大化窗口时，请指定窗口的左上角的位置。  
  
 *rcNormalPosition*  
 当窗口处于正常 （还原） 的位置，请指定窗口的坐标。  
  
## <a name="requirements"></a>惠?  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

