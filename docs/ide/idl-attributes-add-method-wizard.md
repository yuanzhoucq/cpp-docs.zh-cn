---
title: "“添加方法向导”-&gt;“IDL 特性” | Microsoft Docs"
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
  - "vc.codewiz.method.idlattrib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "添加方法向导 [C++]"
  - "IDL 特性，添加方法向导"
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “添加方法向导”-&gt;“IDL 特性”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用“添加方法向导”的该页为方法指定任何接口定义语言 \(IDL\) 设置。  
  
 **id**  
 设置标识方法的数值 ID。  请参见“MIDL 参考”中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 该框不可用于自定义接口和 MFC 调度接口。  
  
 **call\_as**  
 指定该本地方法可以映射为的远程方法的名称。  请参见“MIDL 参考”中的 [call\_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)。  
  
 不可用于 MFC 调度接口。  
  
 **helpcontext**  
 指定一个上下文 ID，该 ID 使用户可以在帮助文件中查看有关此方法的信息。  请参见“MIDL 参考”中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 不可用于 MFC 调度接口。  
  
 **helpstring**  
 指定一个字符串，该字符串用来描述它所应用的元素。  默认情况下，该字符串设置为“method *Method name*”。请参见“MIDL 参考”中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
 不可用于 MFC 调度接口。  
  
 **其他特性**  
 不可用于 MFC 调度接口。  
  
|特性|说明|  
|--------|--------|  
|**hidden**|指示该方法虽存在，但不应显示在面向用户的浏览器中。  请参见“MIDL 参考”中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**source**|指示方法的成员是事件源。  请参见“MIDL 参考”中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|`local`|向 MIDL 编译器指定方法不是远程的。  请参见“MIDL 参考”中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
|**restricted**|指定方法不能任意调用。  请参见“MIDL 参考”中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|**vararg**|指定方法采用的参数数目可变。  为实现此目的，最后一个参数必须是包含所有其余参数的 **VARIANT** 类型的安全数组。  请参见“MIDL 参考”中的 [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)。|  
  
## 请参阅  
 [添加方法](../ide/adding-a-method-visual-cpp.md)   
 [添加方法向导](../ide/add-method-wizard.md)