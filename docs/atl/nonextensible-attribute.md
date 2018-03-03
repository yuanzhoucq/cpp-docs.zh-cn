---
title: "nonextensible 特性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af16748bb3b2048ce854ccc7a03b2400039184a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nonextensible-attribute"></a>nonextensible 特性
如果双重接口不会扩展在运行时 (即，不会提供方法或属性通过**idispatch:: Invoke**未提供通过 vtable 的)，则应该应用**nonextensible**向接口定义的属性。 此属性提供可用来启用在编译时的完整代码验证的客户端语言 （如 Visual Basic 中) 的信息。 如果未提供此属性，bug 可能仍然在客户端代码隐藏直到运行时。  
  
 有关详细信息**nonextensible**属性和示例，请参阅[nonextensible](../windows/nonextensible.md)。  
  
## <a name="see-also"></a>请参阅  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

