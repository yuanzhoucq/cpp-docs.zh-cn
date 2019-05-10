---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: b10d7bccae6fa9b86d072b8e13791f23516b2c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230714"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand`类是提供程序命令对象的实现。 它提供用于实现`IAccessor`， `ICommandText`，和`ICommandProperties`接口。 `IAccessor`接口是相同的行集中的一个。 命令对象使用访问器来指定参数的绑定。 行集对象使用它们来指定输出列的绑定。 `ICommandText`接口是有用的方式以文本上指定的命令。 此示例使用`ICommandText`更高版本时添加自定义代码的接口; 它还重写`ICommand::Execute`方法。 `ICommandProperties`接口处理所有的命令和行集对象的属性。

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

`IAccessor`接口管理命令和行集合中使用的所有绑定。 使用者可调用`IAccessor::CreateAccessor`与数组`DBBINDING`结构。 每个`DBBINDING`结构包含有关应如何处理列绑定 （如类型和长度） 的信息。 提供程序接收结构，然后确定应如何传输数据以及是否需要任何转换。 `IAccessor`接口用于命令对象中，以处理命令中的任何参数。

命令对象还提供了实现`IColumnsInfo`。 OLE DB 要求`IColumnsInfo`接口。 此接口允许使用者从该命令中检索有关参数的信息。 行集对象使用`IColumnsInfo`接口以返回到提供程序的输出列的信息。

提供程序还包含一个称为接口`IObjectWithSite`。 `IObjectWithSite`接口在 ATL 2.0 中实现，并允许实施者可以将有关其自身的信息传递给其子级。 命令对象使用`IObjectWithSite`的信息，告知任何生成行集对象是谁创建它们。

## <a name="see-also"></a>请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)