---
title: "COM 映射宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1c8e73fc4d6cab2e9052e74d68bddbb5796ebfa8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="com-map-macros"></a>COM 映射宏
这些宏定义 COM 接口映射。  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|将 COM 接口映射条目的开始标记。|  
|[END_COM_MAP](#end_com_map)|标记 COM 接口映射条目的末尾。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
   
##  <a name="begin_com_map"></a>BEGIN_COM_MAP  
 COM 映射是公开的对象通过在客户端上的接口的机制`QueryInterface`。  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]你将在公开接口的类对象的名称。  
  
### <a name="remarks"></a>备注  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)只返回中的 COM 映射的接口的指针。 开始使用你接口映射`BEGIN_COM_MAP`宏，为每个具有你接口添加条目[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)宏或其任一变体，并完成对地图[END_COM_MAP](#end_com_map)宏。  

  
### <a name="example"></a>示例  
 与 ATL[寻呼机](../../visual-cpp-samples.md)示例︰  
  
 [!code-cpp[NVC_ATL_COM #1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 结束 COM 接口映射的定义。  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [COM 映射全局函数](../../atl/reference/com-map-global-functions.md)

