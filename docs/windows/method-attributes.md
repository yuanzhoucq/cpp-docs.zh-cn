---
title: 方法特性 |Microsoft 文档
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
ms.openlocfilehash: 9d2efe55058ab2ace7530afee7255b2ba08377b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879817"
---
# <a name="method-attributes"></a>方法特性
以下属性将应用于类、 组件类或接口中的方法。  
  
|特性|描述|  
|---------------|-----------------|  
|[bindable](../windows/bindable.md)|指示属性支持数据绑定。|  
|[call_as](../windows/call-as.md)|允许不可远程控制函数映射到远程函数。|  
|[custom](../windows/custom-cpp.md)|你可以定义自己的属性。|  
|[db_column](../windows/db-column.md)|将指定的列绑定到行集。|  
|[db_command](../windows/db-command.md)|创建 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|将指定的成员变量与一个输入或输出参数相关联，并分隔变量。|  
|[db_source](../windows/db-source.md)|创建与数据源的连接。|  
|[db_table](../windows/db-table.md)|将打开一个 OLE DB 表。|  
|[defaultbind](../windows/defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用于 Visual Basic 代码优化。|  
|[displaybind](../windows/displaybind.md)|指示应显示给用户作为可绑定的属性。|  
|[helpcontext](../windows/helpcontext.md)|指定允许用户查看有关此帮助文件中的元素信息的上下文 ID。|  
|[helpfile](../windows/helpfile.md)|设置类型库的帮助文件的名称。|  
|[helpstring](../windows/helpstring.md)|指定用于描述应用于元素的字符字符串。|  
|[helpstringcontext](../windows/helpstringcontext.md)|.Hlp 或.chm 文件中指定的帮助主题的 ID。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） 的 dll 的名称。|  
|[hidden](../windows/hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|  
|[id](../windows/id.md)|指定的成员函数 （属性或方法，在接口或调度接口） DISPID。|  
|[immediatebind](../windows/immediatebind.md)|指示数据库将立即收到通知的数据绑定对象的属性的所有更改。|  
|[in](../windows/in-cpp.md)|指示参数是要调用的过程中传递给调用的过程。|  
|[local](../windows/local-cpp.md)|可用作接口标头中使用时的标头生成器 MIDL 编译器。 当使用单个函数中，指定为其生成没有存根 （stub） 的本地过程。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|  
|[propget](../windows/propget.md)|指定的属性访问器函数。|  
|[propput](../windows/propput.md)|指定的属性设置函数。|  
|[propputref](../windows/propputref.md)|指定使用的引用，而不是值的属性设置函数。|  
|[ptr](../windows/ptr.md)|将一个指针指定为完整的指针。|  
|[范围](../windows/range-cpp.md)|指定自变量或在运行时设置其值的字段的允许值的范围。|  
|[requestedit](../windows/requestedit.md)|该值指示属性是否支持**OnRequestEdit**通知。|  
|[restricted](../windows/restricted.md)|指定不能任意调用模块、 接口或调度接口的成员。|  
|[satype](../windows/satype.md)|指定的数据类型**SAFEARRAY**结构。|  
|[源](../windows/source-cpp.md)|指定控件的连接点的源接口的类上。 属性或方法上,**源**属性指示的成员返回的对象或作为源的事件的变体。|  
|[synchronize](../windows/synchronize.md)|将对目标方法的访问进行同步。|  
|[vararg](../windows/vararg.md)|指定该函数采用数目可变的参数。|  
  
## <a name="see-also"></a>请参阅  
 [按用法分的特性](../windows/attributes-by-usage.md)