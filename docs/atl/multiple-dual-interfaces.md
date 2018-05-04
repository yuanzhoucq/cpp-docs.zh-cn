---
title: 多个双重接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23682bd0b7c923a1e377463405f84a6c6ee1221
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="multiple-dual-interfaces"></a>多个双重接口
你可能想要将双重接口 （即，vtable 和后期绑定，因此使类可用于脚本语言，以及 c + + 的灵活性） 优点结合起来使用多重继承的技术。  
  
 尽管很可能会公开单个 COM 对象上的多个双重接口，但不建议。 如果有多个双重接口，必须有一个`IDispatch`公开接口。 可用于确保这种情况的方法执行例如函数或提高的代码复杂性丢失而受到处罚。 优点和缺点，开发人员考虑这种方法应仔细权衡来衡量。  
  
## <a name="exposing-a-single-idispatch-interface"></a>公开一个单一的 IDispatch 接口  
 可以通过从两个或多个专用化派生公开对单个对象的多个双重接口`IDispatchImpl`。 但是，如果你允许客户端查询`IDispatch`接口，你将需要使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)宏 (或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) 来指定要用于的基类实现`IDispatch`。  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 因为只有一个`IDispatch`接口公开时，只能访问你通过对象的客户端`IDispatch`接口将无法访问的方法或任何其他接口中的属性。  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>将多个双重接口组合成单个实现的 IDispatch  
 ATL 不提供任何支持将多个双重接口组合到单个实现的`IDispatch`。 但是，有几种已知的方法手动组合的接口，如创建一个包含的单独的联合的模板化类`IDispatch`接口，创建一个新对象来执行`QueryInterface`函数，或使用基于 typeinfo 的嵌套对象，若要创建实现`IDispatch`接口。  
  
 这些方法都有潜在的命名空间冲突，以及代码复杂性和可维护性问题。 建议不要创建多个双重接口。  
  
## <a name="see-also"></a>请参阅  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

