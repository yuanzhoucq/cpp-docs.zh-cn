---
title: "复合控件宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
dev_langs: C++
helpviewer_keywords: composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 154c8f30e1d0141af7c0825d5af1208b95881a86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="composite-control-macros"></a>复合控件宏
这些宏定义事件接收器映射和条目。  
  
|||  
|-|-|  
|[BEGIN_SINK_MAP](#begin_sink_map)|标记复合控件事件接收器映射的开始。|  
|[END_SINK_MAP](#end_sink_map)|标记复合控件事件接收器映射的末尾。|  
|[SINK_ENTRY](#sink_entry)|事件接收器映射到的项。|  
|[SINK_ENTRY_EX](#sink_entry_ex)|进入事件接收器映射另外提供一个参数。| 
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017)与 SINK_ENTRY_EX 类似，但前者将指向 iid 的指针。|  
|[SINK_ENTRY_INFO](#sink_entry_info)|事件接收器映射的用于手动提供的类型信息进入[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)。|  
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017)与 SINK_ENTRY_INFO 类似，但前者将指向 iid 的指针。|  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP  
 声明的复合控件事件接收器映射的开头。  
  
```
BEGIN_SINK_MAP(_class)
```  
  
### <a name="parameters"></a>参数  
 `_class`  
 [in]指定的控件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>备注  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
##  <a name="end_sink_map"></a>END_SINK_MAP  
 声明为复合控件事件接收器映射的末尾。  
  
```
END_SINK_MAP()
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>备注  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
##  <a name="sink_entry"></a>SINK_ENTRY  
 声明处理程序函数 ( `fn`) 为指定的事件 ( `dispid`)，标识的控件的`id`。  
  
```
SINK_ENTRY( id, dispid, fn )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识控件。  
  
 `dispid`  
 [in]标识指定的事件。  
  
 `fn`  
 [in]事件处理程序函数的名称。 此函数必须使用**_stdcall**调用约定，并且具有适当的调度接口样式的签名。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>备注  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX 和 SINK_ENTRY_EX_P
 声明处理程序函数 ( `fn`) 为指定的事件 ( `dispid`) 的调度接口 ( *iid)*，由该控件的`id`。  
  
```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识控件。  
  
 `iid`  
 [in]标识的调度接口。  

 `piid`  
 [in]指向调度接口指针。  
  
 `dispid`  
 [in]标识指定的事件。  
  
 `fn`  
 [in]事件处理程序函数的名称。 此函数必须使用**_stdcall**调用约定，并且具有适当的调度接口样式的签名。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]  
  
### <a name="remarks"></a>备注  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO 和 SINK_ENTRY_INFO_P  
 使用`SINK_ENTRY_INFO`事件接收器映射以提供所需的信息中的宏[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)将事件路由到相关的处理程序函数。  
  
```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识事件源的无符号的整数。 此值必须匹配`nID`相关中使用的模板参数[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基类。  
  
 `iid`  
 [in]标识的调度接口的 IID。  

 `piid`  
 [in]指针，指向标识的调度接口的 IID。
  
 `dispid`  
 [in]DISPID 标识指定的事件。  
  
 `fn`  
 [in]事件处理程序函数的名称。 此函数必须使用**_stdcall**调用约定，并且具有适当的调度接口样式的签名。  
  
 `info`  
 [in]类型的事件处理程序函数的信息。 此类型信息提供的指针的形式`_ATL_FUNC_INFO`结构。 `CC_CDECL`是在 Windows CE 中受支持的唯一选项`CALLCONV`字段`_ATL_FUNC_INFO`结构。 任何其他值不受支持因此其行为未定义。  
  
### <a name="remarks"></a>备注  
 前四个宏参数是否为相同[SINK_ENTRY_EX](#sink_entry_ex)宏。 最后一个参数提供事件的类型的信息。 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  

## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [复合控件全局函数](../../atl/reference/composite-control-global-functions.md)
