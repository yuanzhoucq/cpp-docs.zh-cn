---
title: 实现 CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197466"
---
# <a name="implementing-ccomobjectrootex"></a>实现 CComObjectRootEx

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)是必不可少的; 所有 ATL 对象必须都具有的一个实例`CComObjectRootEx`或[CComObjectRoot](../atl/reference/ccomobjectroot-class.md)在其继承。 `CComObjectRootEx` 提供基于 COM 映射项的默认 `QueryInterface` 机制。

通过其 COM 映射，对象的接口将在客户端查询接口时向该客户端公开。 该查询通过 `CComObjectRootEx::InternalQueryInterface` 执行。 `InternalQueryInterface` 仅处理 COM 映射表中的接口。

接口可以输入到 COM 映射表与[COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry)宏或其一个变体。 例如，以下代码输入可将接口 `IDispatch`、`IBeeper` 和 `ISupportErrorInfo` 输入到 COM 映射表：

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>请参阅

[ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)<br/>
[COM 映射宏](../atl/reference/com-map-macros.md)
