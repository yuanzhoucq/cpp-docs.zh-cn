---
title: "IAxWinAmbientDispatchEx Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IAxWinAmbientDispatchEx"
  - "IAxWinAmbientDispatchEx"
  - "ATL::IAxWinAmbientDispatchEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinAmbientDispatchEx interface"
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# IAxWinAmbientDispatchEx Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此接口实现一个承载的控件的补充环境属性。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      MIDL_INTERFACE( "B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5" )  
IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[SetAmbientDispatch](../Topic/IAxWinAmbientDispatchEx::SetAmbientDispatch.md)|此方法调用添加与用户定义的接口的默认环境属性接口。|  
  
## 备注  
 包括该接口在与ATL静态链接并承载ActiveX控件的ATL应用程序，但环境属性特别是的ActiveX控件。  不要包含此接口将生成该断言:“忘记通过LIBID到CComModule::Init?”  
  
 此接口由ATL的承载对象的ActiveX控件显示。  从 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)派生，`IAxWinAmbientDispatchEx` 添加允许您向ATL提供的单个属性接口与自己的方法。  
  
 [AXHost](https://msdn.microsoft.com/en-us/library/system.windows.forms.axhost.aspx) 将尝试从包含代码的类型库加载有关 `IAxWinAmbientDispatch` 和 `IAxWinAmbientDispatchEx` 的类型信息。  
  
 如果使用ATL90.dll链接，**AXHost** 从类型库将加载该类型信息在DLL。  
  
 有关详细信息 [承载使用ATL AXHost的ActiveX控件](../../atl/hosting-activex-controls-using-atl-axhost.md) 参见。  
  
## 要求  
 此接口的定义的多种形式，如下表所示。  
  
|定义类型|文件|  
|----------|--------|  
|IDL|atliface.idl|  
|类型库|ATL.dll|  
|C\+\+|atliface.h \(也包括在ATLBase.h\)|  
  
## 请参阅  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)