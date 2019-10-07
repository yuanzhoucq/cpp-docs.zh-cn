---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: de2762cff3d697261e159336d866a5a7cb10fafa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492008"
---
# <a name="queryinterface"></a>QueryInterface

尽管有一些机制可以使对象以静态方式 (在实例化之前) 提供它所提供的功能, 但基本的 COM 机制是使用`IUnknown`称为[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))的方法。

每个接口均派生`IUnknown`自, 因此每个接口都有`QueryInterface`一个实现。 无论实现如何, 此方法都使用调用方想要指针的接口的 IID 来查询对象。 如果对象支持该接口, `QueryInterface`则检索指向接口的指针, 同时调用。 `AddRef` 否则, 它将返回 E_NOINTERFACE 错误代码。

请注意, 必须始终遵守[引用计数](../atl/reference-counting.md)规则。 如果在接口`Release`指针上调用以将引用计数递减为零, 则不应再次使用该指针。 偶尔, 你可能需要获取对某个对象的弱引用 (即, 你可能希望获取指向其接口之一的指针而不增加引用计数), 但通过调用`QueryInterface` `Release`后跟, 此操作是不可行的。 以这种方式获取的指针无效, 不应使用。 定义[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)后, 这会变得明显明显, 因此, 定义此宏是查找引用计数 bug 的有用方法。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[QueryInterface在对象中导航](/windows/win32/com/queryinterface--navigating-in-an-object)
