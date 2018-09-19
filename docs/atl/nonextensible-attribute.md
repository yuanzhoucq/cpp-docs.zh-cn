---
title: nonextensible 特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73edae463051aca3ecafac53ae6200df103b8d90
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762136"
---
# <a name="nonextensible-attribute"></a>nonextensible 特性

如果双重接口不会扩展在运行时 (即，不会提供方法或通过属性`IDispatch::Invoke`，不可通过 vtable)，则应该应用**nonextensible**向导向接口属性定义。 此属性提供可用于启用完整的代码在编译时验证的客户端语言 （如 Visual Basic 中) 的信息。 如果未提供此特性，bug 可能仍然在客户端代码中隐藏到运行时。

有关详细信息**nonextensible**属性和示例，请参阅[nonextensible](../windows/nonextensible.md)。

## <a name="see-also"></a>请参阅

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

