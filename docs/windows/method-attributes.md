---
title: 方法特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1850507b9d00ab717a2602d4e230968f5222f077
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604276"
---
# <a name="method-attributes"></a>方法特性
以下属性应用于类、 组件类或接口中的方法。  
  
|特性|描述|  
|---------------|-----------------|  
|[bindable](../windows/bindable.md)|指示该属性支持数据绑定。|  
|[call_as](../windows/call-as.md)|允许不可远程处理函数映射到远程函数。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[defaultbind](../windows/defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|  
|[displaybind](../windows/displaybind.md)|指示应显示给用户作为可绑定的属性。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素的信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstring](../windows/helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|  
|[helpstringcontext](../windows/helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[id](../windows/id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|  
|[immediatebind](../windows/immediatebind.md)|指示数据库将立即收到通知的所有更改将数据绑定对象的属性。|  
|[in](../windows/in-cpp.md)|指示参数是要从调用过程传递给被调用过程。|  
|[local](../windows/local-cpp.md)|可以使用 MIDL 编译器为标头生成器界面标头中使用时。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|  
|[propget](../windows/propget.md)|指定的属性访问器函数。|  
|[propput](../windows/propput.md)|指定的属性设置函数。|  
|[propputref](../windows/propputref.md)|指定使用引用而不是值的属性设置函数。|  
|[ptr](../windows/ptr.md)|将一个指针，指定为完整的指针。|  
|[范围](../windows/range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|  
|[requestedit](../windows/requestedit.md)|指示该属性支持`OnRequestEdit`通知。|  
|[restricted](../windows/restricted.md)|指定不能任意调用模块、 接口或调度接口的成员。|  
|[satype](../windows/satype.md)|指定的数据类型`SAFEARRAY`结构。|  
|[source](../windows/source-cpp.md)|指定连接点的控件的源接口的类上。 在属性或方法，`source`属性指示该成员返回的对象或为事件源的变体。|  
|[synchronize](../windows/synchronize.md)|同步到目标方法的访问。|  
|[vararg](../windows/vararg.md)|指定该函数采用数量可变的参数。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)