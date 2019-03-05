---
title: 创建聚合的对象
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 4be8d0e852da91b58125dc01d44eed4560b2b8d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277516"
---
# <a name="creating-an-aggregated-object"></a>创建聚合的对象

聚合委托`IUnknown`调用，提供指向外部对象的指针`IUnknown`内部对象。

## <a name="to-create-an-aggregated-object"></a>若要创建聚合的对象

1. 添加`IUnknown`指向您的类对象，并在构造函数中将其初始化为 NULL。

1. 重写[FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct)创建聚合函数。

1. 使用`IUnknown`指针，在步骤 1 中定义的第二个参数为[COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate)宏。

1. 重写[FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease)释放`IUnknown`指针。

> [!NOTE]
> 如果你使用和发布期间聚合的对象中的接口。 `FinalConstruct`，则应将添加[DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct)到类对象定义的宏。

## <a name="see-also"></a>请参阅

[ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)
