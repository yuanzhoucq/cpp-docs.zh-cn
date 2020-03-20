---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 61bd60b63490303c65729843c3c0351a570a8056
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545725"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand` 类是提供程序命令对象的实现。 它提供 `IAccessor`、`ICommandText`和 `ICommandProperties` 接口的实现。 `IAccessor` 接口与行集中的接口相同。 Command 对象使用访问器指定参数的绑定。 行集对象使用它们来指定输出列的绑定。 `ICommandText` 接口是一种以一种方式指定命令的有效方法。 此示例稍后在添加自定义代码时使用 `ICommandText` 接口;它还覆盖 `ICommand::Execute` 方法。 `ICommandProperties` 接口处理命令和行集对象的所有属性。

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

`IAccessor` 接口管理命令和行集中使用的所有绑定。 使用者使用 `DBBINDING` 结构的数组调用 `IAccessor::CreateAccessor`。 每个 `DBBINDING` 结构都包含有关应如何处理列绑定（如类型和长度）的信息。 提供程序接收结构，然后确定应该如何传输数据以及是否需要进行任何转换。 `IAccessor` 接口用于在命令对象中处理命令中的任何参数。

Command 对象还提供 `IColumnsInfo`的实现。 OLE DB 要求 `IColumnsInfo` 接口。 接口允许使用者从命令检索有关参数的信息。 行集对象使用 `IColumnsInfo` 接口将有关输出列的信息返回给提供程序。

提供程序还包含名为 `IObjectWithSite`的接口。 在 ATL 2.0 中实现了 `IObjectWithSite` 接口，并允许实施者将自己的信息传递到其子级。 Command 对象使用 `IObjectWithSite` 信息告诉任何生成的行集对象。

## <a name="see-also"></a>另请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)