---
title: 参考计数 （ATL）
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321745"
---
# <a name="reference-counting"></a>参考计数

当 COM 本身认为对象不再被使用时，不会自动尝试从内存中删除该对象。 相反，对象程序员必须删除未使用的对象。 程序员根据引用计数确定是否可以删除对象。

COM 使用`IUnknown` [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)的方法来管理对象上接口的引用计数。 调用这些方法的一般规则是：

- 每当客户端收到接口指针时，`AddRef`都必须在接口上调用。

- 每当客户端完成使用接口指针时，它必须调用`Release`。

在简单实现中，每个`AddRef`调用都会`Release`递减对象内的计数器变量。 当计数返回零时，接口不再具有任何用户，并且可以自由地从内存中删除自身。

还可以实现引用计数，以便计算对对象的每个引用（而不是单个接口）。 在这种情况下，每个`AddRef`对象调用`Release`委托到对象的中央实现，并在`Release`对象的引用计数达到零时释放整个对象。

> [!NOTE]
> 使用新`CComObject`运算符构造派生对象时，引用**new**计数为 0。 因此，在成功创建`AddRef``CComObject`派生对象后，必须调用 。

## <a name="see-also"></a>另请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[通过引用计数管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
