---
title: QueryInterface |Microsoft 文档
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
ms.openlocfilehash: cde92ee56e51a86acbfb7e459571291bc3cae76c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="queryinterface"></a>QueryInterface
虽然有一个对象可以依据 express 它提供了静态 （它是在实例化之前） 的功能的机制，但基本的 COM 机制是使用**IUnknown**调用方法[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 每个接口派生自**IUnknown**，因此每个接口有的实现`QueryInterface`。 不考虑实现，此方法将查询使用向其调用方想指针的接口的 IID 的对象。 如果对象支持该接口，`QueryInterface`还调用时检索到该接口的指针`AddRef`。 否则，它将返回**E_NOINTERFACE**错误代码。  
  
 请注意，必须遵循[引用计数](../atl/reference-counting.md)在所有时间的规则。 如果调用**版本**上以减少为零的引用计数的接口指针，则不应使用该指针试。 有时你可能需要获取对对象的弱引用 （即，你可能想要不递增引用计数的情况下获取指向其接口之一的指针），但它不是可接受，若要执行此操作通过调用`QueryInterface`跟**版本**。 在这种方式中获得的指针无效，不应使用。 这更容易会了然-时[_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces)定义的因此定义此宏是查找引用计数 bug 的有效方法。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [QueryInterface： 对象中导航](http://msdn.microsoft.com/library/windows/desktop/ms687230)

