---
title: QueryInterface |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff08e5f527d9ef1be99b788ef05beb7ef58da53b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752527"
---
# <a name="queryinterface"></a>QueryInterface

虽然有依据对象可以表示它提供以静态方式 （它实例化之前） 的功能的机制，但基本的 COM 机制是使用`IUnknown`方法调用[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))。

每个接口派生自`IUnknown`，因此每个接口的实现`QueryInterface`。 无论实现中，此方法将查询使用向其调用方想指针的接口的 IID 的对象。 如果对象支持该接口`QueryInterface`同时调用检索指向接口的指针`AddRef`。 否则，它将返回 E_NOINTERFACE 错误代码。

请注意，必须遵循[引用计数](../atl/reference-counting.md)规则应用于所有时间。 如果调用`Release`上要递减引用计数为零的接口指针，则不应使用该指针试。 有时您可能需要获取对对象的弱引用 （即，您可能想要获取指向其中一个接口的指针不递增引用计数的情况下），但它不是可接受，若要执行此操作通过调用`QueryInterface`跟`Release`。 在这种方式获取的指针无效，不应使用。 这更轻松地变得明显时[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)定义的因此定义此宏是查找引用计数错误的有效方法。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)   
[在对象中导航的 QueryInterface:](/windows/desktop/com/queryinterface--navigating-in-an-object)

