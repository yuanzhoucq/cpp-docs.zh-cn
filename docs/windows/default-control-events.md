---
title: "默认控件事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8f85e534892cf45987cf563f968ca5e1ec28262
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="default-control-events"></a>默认控件事件
下面的控件名称具有随附的默认事件：  
  
|控件名称|默认事件|  
|------------------|-------------------|  
|动画|**ACN_START**|  
|复选框|**BN_CLICKED**|  
|组合框|**CBN_SELCHANGE**|  
|自定义|**TTN_GETDISPINFO**|  
|日期时间选取器|**DTN_DATETIMECHANGE**|  
|编辑框|**EN_CHANGE**|  
|分组框|（不适用）|  
|热键|**NM_OUTOFMEMORY**|  
|IP 地址|**IPN_FIELDCHANGED**|  
|列表|**LVN_ITEMCHANGE**|  
|列表框|**LBN_SELCHANGE**|  
|月历|**MCN_SELCHANGE**|  
|图片控件|（不适用）|  
|进度|**NM_CUSTOMDRAW**|  
|下压按钮|**BN_CLICKED**|  
|单选按钮|**BN_CLICKED**|  
|丰富的编辑|**EN_CHANGE**|  
|滚动条|**NM_THEMECHANGED**|  
|Slider|**NM_CUSTOMDRAW**|  
|数值调节钮|**UDN_DELTAPOS**|  
|静态文本|（不适用）|  
|Tab|**TCN_SELCHANGE**|  
|树|**TVN_SELCHANGE**|  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>另请参阅  
 [为对话框控件定义成员变量](../windows/defining-member-variables-for-dialog-controls.md)   
 [与用户界面对象关联的消息类型](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [编辑消息处理程序](../mfc/reference/editing-a-message-handler.md)   
 [为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [声明基于新控件类的变量](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)

