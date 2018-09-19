---
title: 引用计数 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9288eda15b0bac3d3694ee56a2f427aefb60e032
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086429"
---
# <a name="reference-counting"></a>引用计数

COM 本身不会自动尝试从内存中移除对象时它认为不再使用的对象。 相反，该对象的程序员必须删除未使用的对象。 程序员确定是否可以删除对象根据引用计数。

COM 用途`IUnknown`方法， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)，以管理对某个对象的接口的引用计数。 调用这些方法的一般规则是：

- 每当在客户端接收的接口指针，`AddRef`必须调用该接口上。

- 每当客户端已完成使用的接口指针，它必须调用`Release`。

在简单实现中，每个`AddRef`递增和每个调用`Release`调用递减一个计数器变量对象中的。 计数将返回到零，接口不再有任何用户，且免费从内存中删除其自身。

引用计数还可以实现，以便 （不到一个单独的接口） 的对象的每次引用计数。 在这种情况下，每个`AddRef`并`Release`对象，调用委托给中央实现和`Release`时其引用计数达到零时释放整个对象。

> [!NOTE]
>  当`CComObject`的派生的对象使用构造**新**运算符，引用计数为 0。 因此，调用`AddRef`必须已成功创建后进行`CComObject`-派生的对象。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[管理对象生存期通过引用计数](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)

