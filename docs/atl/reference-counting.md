---
title: 引用计数 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 565b74956280d4e80c41376ead4249e69980a80e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492225"
---
# <a name="reference-counting"></a>引用计数

当某个对象认为不再使用该对象时, COM 本身不会自动尝试从内存中删除该对象。 相反, 对象程序员必须删除未使用的对象。 程序员根据引用计数确定是否可以移除对象。

COM 使用`IUnknown` [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)方法来管理对象上的接口的引用计数。 调用这些方法的一般规则是:

- 每当客户端收到接口指针时, `AddRef`都必须在接口上调用。

- 当客户端使用接口指针时, 必须调用`Release`。

在简单实现中, 每`AddRef`次调用都会递增`Release` , 每次调用都会减少对象内的计数器变量。 当计数返回为零时, 接口将不再具有任何用户, 并且可以随意将其从内存中删除。

还可以实现引用计数, 以便对对象的每个引用 (而不是单个接口) 进行计数。 在这种情况下`AddRef` , `Release`每个和调用都委托对象的中心实现, `Release`当对象的引用计数达到零时释放整个对象。

> [!NOTE]
>  当使用 new 运算符构造派生对象时, 引用计数为0。 `CComObject` 因此, 在成功创建`AddRef`派生的`CComObject`对象之后, 必须执行对的调用。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[通过引用计数管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
