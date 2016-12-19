---
title: "IDocHostUIHandlerDispatch Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDocHostUIHandlerDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDocHostUIHandlerDispatch interface"
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDocHostUIHandlerDispatch Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对分析和呈现引擎的Microsoft HTML的接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
interface IDocHostUIHandlerDispatch : IDispatch  
  
```  
  
## 成员  
  
### 公共方法  
  
> [!NOTE]
>  链接下表对INet SDK引用 [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx) 接口成员的主题。  `IDocHostUIHandlerDispatch` 确实与 **IDocUIHostHandler**，这种差异该 `IDocHostUIHandlerDispatch` 调度接口，而 **IDocUIHostHandler** 是一个自定义接口。  
  
|||  
|-|-|  
|[\<caps:sentence id\="tgt7" sentenceid\="bbafd0070a97938421603b1ef8409510" class\="tgtSentence"\>EnableModeless\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753253.aspx)|调用从 [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)的MSHTML实现。  并调用MSHTML时显示模式UI。|  
|[\<caps:sentence id\="tgt10" sentenceid\="2cfbfb70fe0af79263134b694d06311c" class\="tgtSentence"\>FilterDataObject\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753254.aspx)|由MSHTML对宿主允许宿主替换MSHTML的数据对象。|  
|[\<caps:sentence id\="tgt12" sentenceid\="715255e2d7f611c97308a373328e19a0" class\="tgtSentence"\>GetDropTarget\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753255.aspx)|调用MSHTML，当它用于，放置目标允许宿主提供替代 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[\<caps:sentence id\="tgt14" sentenceid\="5a51a8633a0d2036f843073d6f35a4af" class\="tgtSentence"\>GetExternal\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753256.aspx)|调用MSHTML获取主机的IDispatch接口。|  
|[\<caps:sentence id\="tgt16" sentenceid\="ce27e0c2f7ebb0aaa2f9088818dc8347" class\="tgtSentence"\>GetHostInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753257.aspx)|检索MSHTML主机的UI功能。|  
|[\<caps:sentence id\="tgt18" sentenceid\="693bd2149b17c4586cdc167e13e59f0a" class\="tgtSentence"\>GetOptionKeyPath\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753258.aspx)|返回下MSHTML存储用户首选项的注册表项。|  
|[\<caps:sentence id\="tgt20" sentenceid\="7fce94585b477684cc21a38fe9ee288c" class\="tgtSentence"\>HideUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753259.aspx)|调用，当MSHTML移除其菜单和工具栏。|  
|[\<caps:sentence id\="tgt22" sentenceid\="359e4dcbd80b962decf88ef02d66fe14" class\="tgtSentence"\>OnDocWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753261.aspx)|调用从 [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)的MSHTML实现。|  
|[\<caps:sentence id\="tgt24" sentenceid\="8e472d7f3f3064d2ee6fdddd83002b86" class\="tgtSentence"\>OnFrameWindowActivate\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753262.aspx)|调用从 [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)的MSHTML实现。|  
|[\<caps:sentence id\="tgt26" sentenceid\="3fd38deec5e9f4201074e886bfb178a5" class\="tgtSentence"\>ResizeBorder\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753263.aspx)|调用从 [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)的MSHTML实现。|  
|[\<caps:sentence id\="tgt28" sentenceid\="2f382ba3de5494d18b20ccfa348f795e" class\="tgtSentence"\>ShowContextMenu\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753264.aspx)|调用从MSHTML显示上下文菜单。|  
|[\<caps:sentence id\="tgt30" sentenceid\="c6978c4c8ab30ae8380439da613bb63c" class\="tgtSentence"\>ShowUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753265.aspx)|允许宿主替换MSHTML菜单和工具栏。|  
|[\<caps:sentence id\="tgt32" sentenceid\="97bfd5aead25a2d9870b38da4b6745cd" class\="tgtSentence"\>TranslateAccelerator\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753266.aspx)|调用MSHTML，当 [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) 或 [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) 调用。|  
|[\<caps:sentence id\="tgt34" sentenceid\="55c20a6fb6b05f6059d72b2854a7d7e2" class\="tgtSentence"\>TranslateUrl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753267.aspx)|调用MSHTML提供宿主有机会修改要加载的URL。|  
|[\<caps:sentence id\="tgt36" sentenceid\="8fdf7c2c3ebf5fa12ecc909279c951ff" class\="tgtSentence"\>UpdateUI\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/aa753268.aspx)|通知宿主顺序状态发生了变化。|  
  
## 备注  
 可以替换菜单、工具栏和上下文菜单使用由Microsoft HTML分析和呈现引擎\(MSHTML\)通过实现宿主此接口。  
  
## 要求  
 此接口的定义可用作IDL或C\+\+，如下所示。  
  
|定义类型|文件|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包括在ATLBase.h\)|  
  
## 请参阅  
 [IDocUIHostHandler](https://msdn.microsoft.com/en-us/library/aa753260.aspx)