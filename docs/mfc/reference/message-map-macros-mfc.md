---
title: "消息映射宏 (MFC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message map macros
- Windows messages [C++], declaration
- demarcating Windows messages
- message maps [C++], macros
- message maps [C++], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: f890e0675be58c8e20e313bea54b4145e2ce0bf3
ms.lasthandoff: 02/24/2017

---
# <a name="message-map-macros-mfc"></a>消息映射宏 (MFC)
为了支持消息映射，MFC 提供了以下宏：  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>消息映射声明和分界宏  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP](http://msdn.microsoft.com/library/c225e7e0-a81b-495c-97f9-3e0aa1f65036)|声明将在类中使用消息映射来将消息映射到函数（必须在类声明中使用）。|  
|[BEGIN_MESSAGE_MAP](http://msdn.microsoft.com/library/d9201e18-04e0-4639-9810-f15768627fc2)|开始消息映射的定义（必须在类实现中使用）。|  
|[END_MESSAGE_MAP](http://msdn.microsoft.com/library/40f611f1-a3b4-4097-b683-091bf7cfab8b)|结束消息映射的定义（必须在类实现中使用）。|  
  
### <a name="message-mapping-macros"></a>消息映射宏  
  
|||  
|-|-|  
|[ON_COMMAND](http://msdn.microsoft.com/library/f24f8bda-2cf4-49d5-aa3d-6f2e6bb003f2)|指示哪个函数将处理指定的命令消息。|  
|[ON_CONTROL](http://msdn.microsoft.com/library/2cb7ebdf-296b-4606-b191-3449835003db)|指示哪个函数将处理指定的控件通知消息。|  
|[ON_MESSAGE](http://msdn.microsoft.com/library/e2faeb13-9f6e-4c0d-9f6d-b2e141a0db1e)|指示哪个函数将处理用户定义的消息。|  
|[ON_OLECMD](http://msdn.microsoft.com/library/6c86327c-3d48-42ac-9dae-e0ccd3a81793)|指示哪个函数将处理 DocObject 或其容器中的菜单命令。|  
|[ON_REGISTERED_MESSAGE](http://msdn.microsoft.com/library/93c1c068-ae8c-4e04-8a60-a603800ab57d)|指示哪个函数将处理已注册的用户定义消息。|  
|[ON_REGISTERED_THREAD_MESSAGE](http://msdn.microsoft.com/library/3f598bc2-b2f0-410f-8ba0-7714502170f3)|指示哪个函数将在您具有 `CWinThread` 类时处理已注册的用户定义消息。|  
|[ON_THREAD_MESSAGE](http://msdn.microsoft.com/library/f718f47a-d5b1-4514-914b-e3fe2d919003)|指示哪个函数将在您具有 `CWinThread` 类时处理用户定义的消息。|  
|[ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4)|指示哪个函数将处理指定的用户界面更新命令消息。|  
  
### <a name="message-map-range-macros"></a>消息映射范围宏  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE](http://msdn.microsoft.com/library/c52719fc-dd6e-48c9-af79-383f48d608e0)|指示哪个函数将处理在宏的前两个参数中指定的命令 ID 的范围。|  
|[ON_UPDATE_COMMAND_UI_RANGE](http://msdn.microsoft.com/library/b7105bf1-44ad-4b00-b947-31478f964729)|指示哪个更新处理程序将处理在宏的前两个参数中指定的命令 ID 的范围。|  
|[ON_CONTROL_RANGE](http://msdn.microsoft.com/library/46f0e1bb-569b-4b8b-9b80-89701d1cd7fd)|指示哪个函数将处理来自在宏的第二个和第三个参数中指定的控件 ID 的范围的通知。 第一个参数是控件通知消息，如**BN_CLICKED**。|  
  
 消息映射、 消息映射声明和分界宏和消息映射宏的详细信息，请参阅[消息映射](../../mfc/reference/message-maps-mfc.md)和[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。 有关消息映射范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。  
  
## <a name="see-also"></a>另请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)



