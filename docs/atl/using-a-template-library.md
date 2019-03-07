---
title: 使用模板库 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
ms.openlocfilehash: 7b1a6b0befcfd7ecf0a150653b5c32239b7f9543
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282664"
---
# <a name="using-a-template-library"></a>使用模板库

模板是有些类似于宏。 与使用宏，调用模板后，即可展开 （使用适当的参数替换） 到您编写的代码。 但是，模板比这更进一步以基于作为参数传递的类型的新类创建。 这些新类实现执行在模板代码中表示该操作的类型安全的方式。

模板库，如 ATL 从传统的 c + + 类库不同之处在于它们通常提供仅作为源代码 （或作为较少，支持运行的时的源代码），并不是本质上是或一定实际上具有层次结构。 而不是派生自类，以获取所需的功能，您实例化模板类。

## <a name="see-also"></a>请参阅

[ATL 简介](../atl/introduction-to-atl.md)
