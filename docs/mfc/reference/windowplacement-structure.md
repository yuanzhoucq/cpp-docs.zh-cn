---
title: "WINDOWPLACEMENT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 62cf7003f43d50d5998dd527ae5ad7b10ab95686
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
 以字节为单位，该结构的指定的长度，**。**  
  
 `flags`  
 指定用于控制最小化的窗口和窗口还原时所依据的方法的位置的标志。 此成员可以是一个或两个以下标志︰  
  
- **WPF_SETMINPOSITION**指定可以指定 x 和 y 的位置的最小化窗口**。** 必须为此标志指定在中设置坐标**ptMinPosition**成员。  
  
- **WPF_RESTORETOMAXIMIZED**指定，还原窗口中将会最大化，无论是否它被最大化之前被最小化。 此设置是有效仅还原窗口中的下一次。 它不会更改默认还原操作行为。 此标志则仅当**SW_SHOWMINIMIZED**为指定值**showCmd**成员。  
  
 *showCmd*  
 指定窗口中的当前显示状态。 此成员可以是下列值之一︰  
  
- **SW_HIDE**隐藏窗口，并将激活传递到另一个窗口。  
  
- **SW_MINIMIZE**最小化指定的窗口，并激活系统的列表中的顶级窗口。  
  
- **SW_RESTORE**激活并显示一个窗口。 如果该窗口已最小化，则最大化，Windows 将其还原到其原始大小和位置 (与相同**SW_SHOWNORMAL**)。  
  
- **SW_SHOW**激活窗口，并将其显示在其当前大小和位置。  
  
- **SW_SHOWMAXIMIZED**激活窗口，并将其显示为最大化的窗口。  
  
- **SW_SHOWMINIMIZED**激活窗口，并将其显示为图标。  
  
- **SW_SHOWMINNOACTIVE**以图标形式显示的窗口。 当前处于活动状态窗口将保持活动状态。  
  
- **SW_SHOWNA**在其当前状态显示一个窗口。 当前处于活动状态窗口将保持活动状态。  
  
- **SW_SHOWNOACTIVATE**显示一个窗口中的最新的大小和位置。 当前处于活动状态窗口将保持活动状态。  
  
- **SW_SHOWNORMAL**激活并显示一个窗口。 如果该窗口已最小化，则最大化，Windows 将其还原到其原始大小和位置 (与相同**SW_RESTORE**)。  
  
 *ptMinPosition*  
 窗口中最小化时指定窗口的左上角的位置。  
  
 `ptMaxPosition`  
 最大化窗口时，请指定窗口的左上角的位置。  
  
 *rcNormalPosition*  
 当窗口处于正常 （还原） 的位置，请指定窗口的坐标。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)


