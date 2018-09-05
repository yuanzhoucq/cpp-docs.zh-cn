---
title: COM 映射宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524f360f2dcc2e1eaec11723395da0be7058c21a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756498"
---
# <a name="com-map-macros"></a>COM 映射宏

这些宏定义 COM 接口映射。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|表示 COM 接口映射项的开头。|
|[END_COM_MAP](#end_com_map)|表示 COM 接口映射项的结尾。|  

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

COM 映射是公开的对象通过在客户端上的接口的机制`QueryInterface`。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>参数

*x*  
[in]你将在公开接口的类对象的名称。

### <a name="remarks"></a>备注

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)仅在 COM 映射中返回的接口指针。 启动与 BEGIN_COM_MAP 宏保持一致的接口映射，您的接口的每个添加的条目[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)宏或其一个变体，并完成对地图[END_COM_MAP](#end_com_map)宏。  

### <a name="example"></a>示例

与 ATL[寻呼机](../../visual-cpp-samples.md)示例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

结束 COM 接口映射的定义。

```
END_COM_MAP()
```

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)   
[COM 映射全局函数](../../atl/reference/com-map-global-functions.md)
