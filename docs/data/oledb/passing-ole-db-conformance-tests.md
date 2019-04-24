---
title: 通过 OLE DB 一致性测试
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: 9f78b16bc30651560137a39286460a8e5ceccd40
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036992"
---
# <a name="passing-ole-db-conformance-tests"></a>通过 OLE DB 一致性测试

为了使提供程序更加一致，数据访问 SDK 提供了一组 OLE DB 一致性测试。 测试检查您的提供程序的所有方面，并为你提供合理的保证，在提供程序按预期方式运行。 您可以在 Microsoft 数据访问 SDK 中找到 OLE DB 一致性测试。 本部分重点介绍应执行通过一致性测试的操作。 有关正在运行的 OLE DB 一致性测试的信息，请参阅 SDK。

## <a name="running-the-conformance-tests"></a>运行一致性测试

视觉对象中C++6.0，OLE DB 提供程序模板添加了大量挂钩函数，以使你能够检查值和属性。 其中的大多数功能已添加以响应对符合性测试。

> [!NOTE]
> 您需要添加多个验证函数，以使提供程序通过 OLE DB 一致性测试。

此提供程序需要两个验证例程。 第一个例程， `CRowsetImpl::ValidateCommandID`，是行集类的一部分。 它是由提供程序模板调用在行集的创建过程。 此示例使用此例程来告诉使用者，它不支持索引。 第一个调用是对`CRowsetImpl::ValidateCommandID`(请注意，在提供程序使用`_RowsetBaseClass`添加的接口映射中的 typedef`CCustomRowset`中[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)，因此不需要键入模板的长行自变量）。 如果索引参数不为 NULL （指示使用者想要使用我们的索引），接下来，返回 DB_E_NOINDEX。 有关命令 Id 的详细信息，请参阅 OLE DB 规范，并查找`IOpenRowset::OpenRowset`。

下面的代码是`ValidateCommandID`验证例程：

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

提供程序模板调用`OnPropertyChanged`方法只要某个用户更改 DBPROPSET_ROWSET 组上的属性。 如果你想要处理的其他组的属性，您将它们添加到适当的对象 (即 DBPROPSET_SESSION 检查进入`CCustomSession`类)。

代码首先检查以查看是否链接到另一个属性。 如果链接属性，它将 DBPROP_BOOKMARKS 属性设置为`True`。 OLE DB 规范的附录 C 包含有关属性的信息。 此信息还将告诉您是否将属性链接到另一个。

您可能还想要添加`IsValidValue`到你的代码例程。 模板调用`IsValidValue`时尝试设置属性。 如果需要额外的处理设置的属性值时，会重写此方法。 您可以为每个属性集的下列方法之一。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)