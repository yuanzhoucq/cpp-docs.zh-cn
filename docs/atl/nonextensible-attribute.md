---
title: nonextensible 特性 |Microsoft 文档
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
ms.openlocfilehash: 40b4b79701862ca07e704aca098419479923ef1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355628"
---
# <a name="nonextensible-attribute"></a>nonextensible 特性
如果双重接口不会扩展在运行时 (即，不会提供方法或属性通过**idispatch:: Invoke**未提供通过 vtable 的)，则应该应用**nonextensible**向接口定义的属性。 此属性提供可用来启用在编译时的完整代码验证的客户端语言 （如 Visual Basic 中) 的信息。 如果未提供此属性，bug 可能仍然在客户端代码隐藏直到运行时。  
  
 有关详细信息**nonextensible**属性和示例，请参阅[nonextensible](../windows/nonextensible.md)。  
  
## <a name="see-also"></a>请参阅  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

