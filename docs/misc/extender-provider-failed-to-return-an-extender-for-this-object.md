---
title: "Extender Provider failed to return an Extender for this object. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTCANTEXTEND"
ms.assetid: 96702669-b720-4076-91b6-bb29ec830a65
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider failed to return an Extender for this object.
未能返回任何扩展程序。  
  
### 更正此错误  
  
1.  验证 IExtenderProvider::CanExtend\(\) 和 IExtenderProvider::GetExtender\(\) 的实现是否成功返回了有效的 Extender 对象。  
  
## 请参阅  
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>