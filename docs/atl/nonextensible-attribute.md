---
title: nonextensible 特性
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257626"
---
# <a name="nonextensible-attribute"></a>nonextensible 特性

如果双重接口不会扩展在运行时 (即，不会提供方法或通过属性`IDispatch::Invoke`，不可通过 vtable)，则应该应用**nonextensible**向导向接口属性定义。 此属性提供可用于启用完整的代码在编译时验证的客户端语言 （如 Visual Basic 中) 的信息。 如果未提供此特性，bug 可能仍然在客户端代码中隐藏到运行时。

有关详细信息**nonextensible**属性和示例，请参阅[nonextensible](../windows/nonextensible.md)。

## <a name="see-also"></a>请参阅

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)
