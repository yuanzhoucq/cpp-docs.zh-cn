---
title: COM 映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326599"
---
# <a name="com-map-macros"></a>COM 映射宏

这些宏定义 COM 接口映射。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|标记 COM 接口映射条目的开头。|
|[END_COM_MAP](#end_com_map)|标记 COM 接口映射条目的末尾。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

COM 映射是通过 向客户端公开对象上的接口的机制`QueryInterface`。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>参数

** x <br/>
[在]要公开接口的类对象的名称。

### <a name="remarks"></a>备注

[CComObjectRootEx：内部查询接口](ccomobjectrootex-class.md#internalqueryinterface)仅返回 COM 映射中接口的指针。 使用BEGIN_COM_MAP宏启动接口映射，使用[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)宏或其变体之一为每个接口添加条目，然后使用[END_COM_MAP](#end_com_map)宏完成映射。

### <a name="example"></a>示例

从 ATL [BEEPER](../../overview/visual-cpp-samples.md)样品中：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

结束 COM 接口映射的定义。

```
END_COM_MAP()
```

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[COM 映射全局函数](../../atl/reference/com-map-global-functions.md)
