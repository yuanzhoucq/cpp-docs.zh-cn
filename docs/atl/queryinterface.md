---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298631"
---
# <a name="queryinterface"></a>QueryInterface

尽管有一些机制可以使对象以静态方式提供它所提供的功能（在实例化之前），但基本的 COM 机制是使用称为[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))的 `IUnknown` 方法。

每个接口都派生自 `IUnknown`，因此每个接口都具有 `QueryInterface`的实现。 无论实现如何，此方法都使用调用方想要指针的接口的 IID 来查询对象。 如果对象支持该接口，`QueryInterface` 会检索指向接口的指针，同时还会调用 `AddRef`。 否则，它将返回 E_NOINTERFACE 错误代码。

请注意，必须始终遵守[引用计数](../atl/reference-counting.md)规则。 如果对接口指针调用 `Release` 以将引用计数递减为零，则不应再次使用该指针。 有时，你可能需要获取对某个对象的弱引用（即，你可能希望获取指向它的某个接口的指针而不增加引用计数），但通过调用 `QueryInterface` 后跟 `Release`不接受此操作。 以这种方式获取的指针无效，不应使用。 定义[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)时，这会变得很明显，因此定义此宏是查找引用计数 bug 的有用方法。

## <a name="see-also"></a>另请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[QueryInterface：在对象中导航](/windows/win32/com/queryinterface--navigating-in-an-object)
