---
title: "OLE 控件类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 类 [C++]"
  - "ActiveX 控件类 [C++]"
  - "ActiveX 控件 [C++], OLE 控件类"
  - "自定义控件 [MFC], 类"
  - "OLE 控件类 [C++]"
  - "OLE 控件 [C++], 类"
  - "可重用组件类"
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 控件类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些是用于，则编写 OLE 控件的主类。  在一个 OLE 控件模块的 `COleControlModule` 类类似于应用程序的类。[CWinApp](../mfc/reference/cwinapp-class.md) 每模块实现一个或多个；OLE 控件这些控件由 `COleControl` 对象表示。  使用 `CConnectionPoint` 对象，这些控件与其容器进行通信。  
  
 而 `COlePropertyPage` 和 `CPropExchange` 类来帮助您实现属性页和属性的控件，`CPictureHolder` 和 `CFontHolder` 类封装图片和字体的 COM 接口。  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 将 OLE 控制模块的 `CWinApp` 类。  从 `COleControlModule` 类派生了 OLE 开发控制模块对象。  为初始化 OLE 控制模块提供成员函数。  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 从 `COleControl` 类派生一开发 OLE 控件。  从 `CWnd`派生，此类都继承一窗口窗口对象的所有功能和额外的 OLE 特定功能，例如事件触发和功能支持方法和属性。  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 `CConnectionPoint` 定义用于与其他 OLE 对象通信的接口（称为“连接点”）的特殊类型。  连接点在其他对象实现可以启动的操作，例如事件触发和更改通知的输出接口。  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 封装 Windows 图片对象和 `IPicture` COM 接口的功能；用于实现 OLE 图片控件的自定义属性。  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 实现常用字体属性并封装 Windows 字体对象和 `IFont` 接口的功能。  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 用于在图形界面（类似于对话框）中显示自定义控件的属性。  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 支持 OLE 控件持久性的实现。  类似于对话框的 [CDataExchange](../mfc/reference/cdataexchange-class.md)。  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 将名字对象也可以构成的对象的字符串表示形式以及同步名字对象是绑定到一名称的流。  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 类似 Works 于 `CMonikerFile`;但是，该异步绑定的对象。名字对象是一名称的流。  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 实现可异步加载的 OLE 控件属性。  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 实现异步传输并在内存文件中缓冲的 OLE 控件属性。  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 接收自在其容器允许活动文档的用户界面的命令 \(如 FileNew，打开，打印，等等\)，并允许在活动文档容器接收自的用户界面的命令。  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 与任意类型和维度的数组一起使用的类。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)