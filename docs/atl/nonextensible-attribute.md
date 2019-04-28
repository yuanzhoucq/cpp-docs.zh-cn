---
title: nonextensible 特性
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: cc57acb8bd7bc3e32c764606da651f57316ceabf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250098"
---
# <a name="nonextensible-attribute"></a>nonextensible 特性

如果双重接口不会扩展在运行时 (即，不会提供方法或通过属性`IDispatch::Invoke`，不可通过 vtable)，则应该应用**nonextensible**向导向接口属性定义。 此属性提供可用于启用完整的代码在编译时验证的客户端语言 （如 Visual Basic 中) 的信息。 如果未提供此特性，bug 可能仍然在客户端代码中隐藏到运行时。

有关详细信息**nonextensible**属性和示例，请参阅[nonextensible](../windows/nonextensible.md)。

## <a name="see-also"></a>请参阅

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)
