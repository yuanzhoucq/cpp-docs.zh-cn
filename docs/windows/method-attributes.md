---
title: "Method Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "method attributes"
  - "attributes [C++], reference topics"
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Method Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下特性应用于类、组件或接口的方法。  
  
|特性|说明|  
|--------|--------|  
|[bindable](../windows/bindable.md)|指示属性支持数据绑定。|  
|[call\_as](../windows/call-as.md)|使一个不可远程控制的函数映射到远程功能。|  
|[custom](../windows/custom-cpp.md)|使您可以定义拥有该属性。|  
|[db\_column](../windows/db-column.md)|将指定的列设置为行集合。|  
|[db\_command](../windows/db-command.md)|创建一个 OLE DB 命令。|  
|[db\_param](../windows/db-param.md)|将指定的成员变量与输入或输出参数并将变量。|  
|[db\_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db\_table](../windows/db-table.md)|打开 OLE DB 表。|  
|[defaultbind](../windows/defaultbind.md)|指示最好地表示对象的唯一，可绑定属性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|  
|[displaybind](../windows/displaybind.md)|指示应向用户显示为可绑定的属性。|  
|[helpcontext](../windows/helpcontext.md)|指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置帮助文件的名称类型库。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，该字符串用来描述它所应用的元素。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在 .hlp 或 .chm 文件指定帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定 DLL 的名称使用执行文档字符串外观 \(本地化\)。|  
|[hidden](../windows/hidden.md)|指示该项目在面向用户的浏览器存在，但不应显示。|  
|[id](../windows/id.md)|用于成员函数 \(一个属性或将方法指定 DISPID，在接口或调度接口\)。|  
|[immediatebind](../windows/immediatebind.md)|指示该数据库将立即得到通知到数据对象属性的任何更改。|  
|[in](../windows/in-cpp.md)|指示参数是从被调用过程传递给被调用过程。|  
|[local](../windows/local-cpp.md)|在接口标头可使用 MIDL 编译器作为页眉生成器，当使用。  当在单个函数，即存根未生成一个本地程序。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员在属性浏览器不应显示。|  
|[propget](../windows/propget.md)|指定属性访问器函数。|  
|[propput](../windows/propput.md)|指定一个属性设置。|  
|[propputref](../windows/propputref.md)|指定使用引用而不是值的属性设置。|  
|[PTR](../windows/ptr.md)|指定指针作为完整的指针。|  
|[范围](../windows/range-cpp.md)|为值设置在运行时的参数或字段指定允许值的大小。|  
|[requestedit](../windows/requestedit.md)|指示属性支持 **OnRequestEdit** 通知。|  
|[restricted](../windows/restricted.md)|指定模块、接口或调度接口的成员不能随机调用。|  
|[satype](../windows/satype.md)|指定 **SAFEARRAY** 结构的数据类型。|  
|[source](../windows/source-cpp.md)|为类指定控件的源接口的连接点。  在属性或方法， **源** 属性指示成员返回作为事件源的对象或变量。|  
|[同步](../windows/synchronize.md)|同步到目标方法。|  
|[vararg](../windows/vararg.md)|指定函数采用参数数目可变。|  
  
## 请参阅  
 [Attributes by Usage](../windows/attributes-by-usage.md)