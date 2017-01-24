---
title: "“添加属性向导”-&gt;“IDL 特性” | Microsoft Docs"
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
  - "vc.codewiz.prop.idlattributes"
dev_langs: 
  - "C++"
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# “添加属性向导”-&gt;“IDL 特性”
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用“添加属性向导”的该页为属性指定任何接口定义语言 \(IDL\) 设置。  
  
 **id**  
 设置标识属性的数值 ID。  该选项不可用于自定义接口的属性。  请参见“MIDL 参考”中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 **helpcontext**  
 指定一个上下文 ID，该 ID 使用户可以在帮助文件中查看有关此属性的信息。  请参见“MIDL 参考”中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 **helpstring**  
 指定一个字符串，该字符串用来描述它所应用的元素。  默认情况下，它设置为“property *属性名*”。请参见“MIDL 参考”中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
## 其他选项  
 并非所有选项都适用于所有属性类型。  
  
|选项|说明|  
|--------|--------|  
|**bindable**|指示属性支持数据绑定。  请参见“MIDL 参考”中的 [bindable](http://msdn.microsoft.com/library/windows/desktop/aa366738)。  对于属性的常用实现，默认情况下设置此选项并且不可更改。|  
|**defaultbind**|指示此单个的可绑定属性能最好地代表对象。  请参见“MIDL 参考”中的 [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790)。|  
|**displaybind**|指示该属性对用户应显示为可绑定。  请参见“MIDL 参考”中的 [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804)。|  
|**immediatebind**|指示将就数据绑定对象的该属性的所有更改立即通知数据库。  请参见“MIDL 参考”中的 [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045)。|  
|**defaultcollelem**|指示属性是默认集合的某个元素的访问函数。  请参见“MIDL 参考”中的 [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792)。|  
|**nonbrowsable**|标记不应显示在属性浏览器中的接口或调度接口成员。  请参见“MIDL 参考”中的 [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117)。|  
|**requestedit**|指示属性支持 **OnRequestEdit** 通知。请参见“MIDL 参考”中的 [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155)。  对于属性的常用实现，默认情况下设置此选项并且不可更改。|  
|**source**|指示属性成员是事件源。  请参见“MIDL 参考”中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|**hidden**|指示属性虽存在，但不应显示在面向用户的浏览器中。  请参见“MIDL 参考”中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**restricted**|指定属性不能任意调用。  请参见“MIDL 参考”中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|`local`|向 MIDL 编译器指定属性不是远程的。  请参见“MIDL 参考”中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
  
## 请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [“添加属性向导”\-\>“名称”](../ide/names-add-property-wizard.md)   
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)   
 [常用属性](../ide/stock-properties.md)