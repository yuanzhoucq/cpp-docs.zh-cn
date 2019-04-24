---
title: 方法特性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023563"
---
# <a name="method-attributes"></a>方法特性

以下属性应用于类、 组件类或接口中的方法。

|特性|描述|
|---------------|-----------------|
|[bindable](bindable.md)|指示该属性支持数据绑定。|
|[call_as](call-as.md)|允许不可远程处理函数映射到远程函数。|
|[custom](custom-cpp.md)|你可以定义自己的属性。|
|[db_column](db-column.md)|将指定的列绑定到行集。|
|[db_command](db-command.md)|创建 OLE DB 命令。|
|[db_param](db-param.md)|指定的成员变量相关联的输入或输出参数和分隔变量。|
|[db_source](db-source.md)|创建与数据源的连接。|
|[db_table](db-table.md)|将打开一个 OLE DB 表。|
|[defaultbind](defaultbind.md)|指示最能代表对象的单个、 可绑定属性。|
|[defaultcollelem](defaultcollelem.md)|用于 Visual Basic 代码优化。|
|[displaybind](displaybind.md)|指示应显示给用户作为可绑定的属性。|
|[helpcontext](helpcontext.md)|指定允许用户查看有关中此元素的信息的上下文 ID**帮助**文件。|
|[helpfile](helpfile.md)|设置的名称**帮助**类型库文件。|
|[helpstring](helpstring.md)|指定一个字符串，用于描述应用该字符串的元素。|
|[helpstringcontext](helpstringcontext.md)|在.hlp 或.chm 文件中指定的帮助主题的 ID。|
|[helpstringdll](helpstringdll.md)|指定要用于执行文档字符串查找 （本地化） DLL 的名称。|
|[hidden](hidden.md)|指示该项存在，但不是应在面向用户的浏览器中显示。|
|[id](id.md)|指定的成员函数 （属性或方法，请在接口或调度接口） 的 DISPID。|
|[immediatebind](immediatebind.md)|指示数据库将立即收到通知的所有更改将数据绑定对象的属性。|
|[in](in-cpp.md)|指示参数是要从调用过程传递给被调用过程。|
|[local](local-cpp.md)|可以使用 MIDL 编译器为标头生成器界面标头中使用时。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。|
|[nonbrowsable](nonbrowsable.md)|指示接口成员不应显示在属性浏览器中。|
|[propget](propget.md)|指定的属性访问器函数。|
|[propput](propput.md)|指定的属性设置函数。|
|[propputref](propputref.md)|指定使用引用而不是值的属性设置函数。|
|[ptr](ptr.md)|将一个指针，指定为完整的指针。|
|[range](range-cpp.md)|指定参数或在运行时设置其值的字段的允许值的范围。|
|[requestedit](requestedit.md)|指示该属性支持 `OnRequestEdit` 通知。|
|[restricted](restricted.md)|指定不能任意调用模块、 接口或调度接口的成员。|
|[satype](satype.md)|指定的数据类型`SAFEARRAY`结构。|
|[source](source-cpp.md)|指定连接点的控件的源接口的类上。 在属性或方法，`source`属性指示该成员返回的对象或为事件源的变体。|
|[synchronize](synchronize.md)|同步到目标方法的访问。|
|[vararg](vararg.md)|指定该函数采用数量可变的参数。|

## <a name="see-also"></a>请参阅

[按用法分的特性](attributes-by-usage.md)