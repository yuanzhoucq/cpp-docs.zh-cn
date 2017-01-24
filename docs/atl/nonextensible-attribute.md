---
title: "nonextensible Attribute | Microsoft Docs"
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
  - "nonextensible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "双重接口, nonextensible attribute"
  - "nonextensible attribute"
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nonextensible Attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果双重接口不是扩展在运行时\(也就是说您不会通过 **IDispatch::Invoke** 通过vtable不可用\)的方法或属性，应将 **nonextensible** 特性应用于接口定义。  此属性提供信息可用于启用完整的代码验证在编译时的客户端语言\(如Visual Basic中为\)。  如果未提供此特性，bug可能仍然保持在运行时客户端代码隐藏。  
  
 有关 **nonextensible** 属性和示例的更多信息，请参见 [nonextensible](../windows/nonextensible.md)。  
  
## 请参阅  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)