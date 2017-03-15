---
title: "COM 映射宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 79658b6ac22719af7172c9d2848675faf2a23a0c
ms.lasthandoff: 02/24/2017

---
# <a name="com-map-macros"></a>COM 映射宏
这些宏定义 COM 接口映射。  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|标记 COM 接口映射项的开头。|  
|[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)|将接口输入到 COM 接口映射。|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏来消除两个分支的继承。|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏来输入到 COM 映射的接口，并指定其 IID。|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，只是您可以指定不同的 IID。|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|该接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 会导致转发到查询`punk`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它将自动创建所描述的聚合`clsid`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 会导致转发到查询`punk`，并且如果`punk`是**NULL**，自动创建所描述的聚合`clsid`。|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|导致你的程序来调用[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)时指定的接口中查询。|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|将保存每个实例的特定于接口的数据。|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|显示您分离式接口。|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|当处理到达此项在 COM 映射时处理的基类的 COM 映射。|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|挂接到 ATL 的一般机制`QueryInterface`逻辑。|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果`func`。|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|返回**E_NOINTERFACE**并终止时为查询的指定的接口的 COM 映射处理。|  
|[END_COM_MAP](#end_com_map)|标记 COM 接口映射项的结尾。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
   
##  <a name="a-namebegincommapa--begincommap"></a><a name="begin_com_map"></a>BEGIN_COM_MAP  
 COM 映射是公开接口通过在客户端对象上的机制`QueryInterface`。  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]要在公开的接口的类对象的名称。  
  
### <a name="remarks"></a>备注  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)只返回中的 COM 映射的接口指针。 启动与您接口映射`BEGIN_COM_MAP`宏，您的接口的每个添加的条目[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5)宏或其一个变体，并完成用映射[END_COM_MAP](#end_com_map)宏。  

  
### <a name="example"></a>示例  
 与 ATL[寻呼机](../../visual-cpp-samples.md)示例︰  
  
 [!code-cpp[NVC_ATL_COM&#1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrymacrosa--cominterfaceentry-macros"></a><a name="com_interface_entry_macros"></a>COM_INTERFACE_ENTRY 宏  
 这些宏对象的接口输入到其 COM 映射，以便可以通过访问这些`QueryInterface`。 中的 COM 映射项的顺序是顺序接口将检查是否已匹配**IID**期间`QueryInterface`。  
  
##  <a name="a-namecominterfaceentry2x2a--cominterfaceentry2"></a><a name="com_interface_entry2_x2"></a>COM_INTERFACE_ENTRY2  
 使用此宏来消除两个分支的继承。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]要从您的对象公开的接口的名称。  
  
 `x2`  
 [in]从其继承分支名称*x*得以实现。  
  
### <a name="remarks"></a>备注  
 例如，如果派生类对象从两个双接口，请您公开`IDispatch`使用`COM_INTERFACE_ENTRY2`由于`IDispatch`可以从任一接口获取。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryiida--cominterfaceentryiid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID  
 使用此宏来输入到 COM 映射的接口，并指定其 IID。  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所公开的接口的 GUID。  
  
 *x*  
 [in]其 vtable 将公开为通过所标识的接口的类名称`iid`。  
  
### <a name="remarks"></a>备注  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&117;](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="a-namecominterfaceentry2iida--cominterfaceentry2iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID  
 与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，只是您可以指定不同的 IID。  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]在指定的接口的 GUID。  
  
 *x*  
 [in]类对象直接派生自接口的名称。  
  
 `x2`  
 [in]第二个接口直接派生自类对象的名称。  
  
### <a name="remarks"></a>备注  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentry2a--cominterfaceentry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2  
 使用此宏来消除两个分支的继承。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]要从您的对象公开的接口的名称。  
  
 `x2`  
 [in]从其继承分支名称*x*得以实现。  
  
### <a name="remarks"></a>备注  
 例如，如果派生类对象从两个双接口，请您公开`IDispatch`使用`COM_INTERFACE_ENTRY2`由于`IDispatch`可以从任一接口获取。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&118;](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="a-namecominterfaceentryaggregate2a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate2"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 该接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询的接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 `punk`假定参数是指向未知的内部对象的聚合或**NULL**，则该项在这种情况下被忽略。 通常情况下，将**CoCreate**中的聚合`FinalConstruct`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryaggregateblinda--cominterfaceentryaggregateblind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 会导致转发到查询`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>参数  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 如果接口查询失败，继续进行处理 COM 映射。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&113;](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  
##  <a name="a-namecominterfaceentryaggregate3a--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate3"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 该接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询的接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 `punk`假定参数是指向未知的内部对象的聚合或**NULL**，则该项在这种情况下被忽略。 通常情况下，将**CoCreate**中的聚合`FinalConstruct`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregatea--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它将自动创建所描述的聚合`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询的接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。 必须是类的包含 COM 映射的成员。  
  
 `clsid`  
 [in]如果将创建的聚合的标识符`punk`是**NULL**。  
  
### <a name="remarks"></a>备注  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentryaggregatea--cominterfaceentryaggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 该接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询的接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 `punk`假定参数是指向未知的内部对象的聚合或**NULL**，则该项在这种情况下被忽略。 通常情况下，将**CoCreate**中的聚合`FinalConstruct`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&112;](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregateblinda--cominterfaceentryautoaggregateblind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 会导致转发到查询`punk`，并且如果`punk`是**NULL**，自动创建所描述的聚合`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>参数  
 `punk`  
 [in]名称**IUnknown**指针。 必须是类的包含 COM 映射的成员。  
  
 `clsid`  
 [in]如果将创建的聚合的标识符`punk`是**NULL**。  
  
### <a name="remarks"></a>备注  
 如果接口查询失败，继续进行处理 COM 映射。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&115;](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="a-namecominterfaceentryautoaggregate2a--cominterfaceentryautoaggregate"></a><a name="com_interface_entry_autoaggregate2"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它将自动创建所描述的聚合`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询的接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。 必须是类的包含 COM 映射的成员。  
  
 `clsid`  
 [in]如果将创建的聚合的标识符`punk`是**NULL**。  
  
### <a name="remarks"></a>备注  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&114;](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="a-namecominterfaceentrybreaka--cominterfaceentrybreak"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK  
 导致你的程序来调用[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)时指定的接口中查询。  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]用于构造的接口标识符的文本。  
  
### <a name="remarks"></a>备注  
 接口中，将通过附加构造 IID *x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentrycachedtearoffa--cominterfaceentrycachedtearoff"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 将保存每个实例的特定于接口的数据。  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]分离式接口的 GUID。  
  
 *x*  
 [in]实现该接口的类的名称。  
  
 `punk`  
 [in]名称**IUnknown**指针。 必须是类的包含 COM 映射的成员。 应初始化为**NULL**类对象的构造函数中。  
  
### <a name="remarks"></a>备注  
 如果未使用该接口，这会降低您的对象的总体实例大小。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#54;](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="a-namecominterfaceentrytearoffa--cominterfaceentrytearoff"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF  
 显示您分离式接口。  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]分离式接口的 GUID。  
  
 *x*  
 [in]实现该接口的类的名称。  
  
### <a name="remarks"></a>备注  
 分离式接口实现，如每次该接口表示实例化一个单独的对象查询的。 通常情况下，您构建您的接口作为拖曳如果很少使用该接口，因为这将 vtable 指针保存在您的主要对象的每个实例。 拖曳时将删除其引用计数变为零。 分离式实现的类应派生自`CComTearOffObjectBase`并且具有其自己 COM 映射。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#1;](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="a-namecominterfaceentrychaina--cominterfaceentrychain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN  
 当处理到达此项在 COM 映射时处理的基类的 COM 映射。  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>参数  
 *类名*  
 [in]当前对象的基类。  
  
### <a name="remarks"></a>备注  
 例如，在下面的代码︰  
  
 [!code-cpp[NVC_ATL_Windowing 排行榜的 #&116;](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 请注意，COM 映射中的第一项必须包含的 COM 映射的对象上的接口。 因此，无法启动与您 COM 映射项`COM_INTERFACE_ENTRY_CHAIN`，这将导致不同的对象要搜索的点的 COM 映射其中**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)**出现在对象的 COM 映射。 如果你想要搜索的另一个对象的 COM 映射，首先，添加的接口条目**IUnknown**到 COM 映射，然后链接对象的 COM 映射。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing #&111;](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentryfunc2a--cominterfaceentryfunc"></a><a name="com_interface_entry_func2"></a>COM_INTERFACE_ENTRY_FUNC  
 挂接到 ATL 的一般机制`QueryInterface`逻辑。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所公开的接口的 GUID。  
  
 `dw`  
 [in]一个参数传递给`func`。  
  
 `func`  
 [in]将返回的函数指针`iid`。  
  
### <a name="remarks"></a>备注  
 如果*iid*匹配查询，该接口则由指定的函数的 IID`func`调用。 该函数的声明应为︰  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 当你的函数调用`pv`指向类对象。 `riid`参数引用，正在查询的接口`ppv`是一个指针指向该函数应存储到该接口指针的位置和`dw`是具有条目中指定的参数。 该函数应设置\*`ppv`到**NULL**并返回**E_NOINTERFACE**或**S_FALSE**如果它选择不返回一个接口。 与**E_NOINTERFACE**，COM 映射处理终止。 与**S_FALSE**，COM 映射处理继续进行，即使不返回了任何接口指针。 如果该函数返回的接口指针，它应返回`S_OK`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentryfuncblinda--cominterfaceentryfuncblind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND  
 与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果`func`。  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>参数  
 `dw`  
 [in]一个参数传递给`func`。  
  
 `func`  
 [in]获取处理 COM 映射中的此项时调用的函数。  
  
### <a name="remarks"></a>备注  
 任何失败将导致处理继续 COM 映射。 如果该函数返回的接口指针，它应返回`S_OK`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentryfunca--cominterfaceentryfunc"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC  
 挂接到 ATL 的一般机制`QueryInterface`逻辑。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所公开的接口的 GUID。  
  
 `dw`  
 [in]一个参数传递给`func`。  
  
 `func`  
 [in]将返回的函数指针`iid`。  
  
### <a name="remarks"></a>备注  
 如果*iid*匹配查询，该接口则由指定的函数的 IID`func`调用。 该函数的声明应为︰  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 当你的函数调用`pv`指向类对象。 `riid`参数引用，正在查询的接口`ppv`是一个指针指向该函数应存储到该接口指针的位置和`dw`是具有条目中指定的参数。 该函数应设置\*`ppv`到**NULL**并返回**E_NOINTERFACE**或**S_FALSE**如果它选择不返回一个接口。 与**E_NOINTERFACE**，COM 映射处理终止。 与**S_FALSE**，COM 映射处理继续进行，即使不返回了任何接口指针。 如果该函数返回的接口指针，它应返回`S_OK`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-namecominterfaceentrynointerfacea--cominterfaceentrynointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE  
 返回**E_NOINTERFACE**并终止时为查询的指定的接口的 COM 映射处理。  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]用于构造的接口标识符的文本。  
  
### <a name="remarks"></a>备注  
 此宏可用于防止在特定情况下使用接口。 例如，可以将此宏插入您的 COM 映射之前`COM_INTERFACE_ENTRY_AGGREGATE_BLIND`以防止对该接口的查询转发到聚合的内部未知。  
  
 接口中，将通过附加构造 IID *x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。  
  
 请参阅[COM_INTERFACE_ENTRY 宏](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)有关 COM 的备注将映射条目。  
  
##  <a name="a-nameendcommapa--endcommap"></a><a name="end_com_map"></a>END_COM_MAP  
 结束 COM 接口映射的定义。  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [COM 映射全局函数](../../atl/reference/com-map-global-functions.md)

