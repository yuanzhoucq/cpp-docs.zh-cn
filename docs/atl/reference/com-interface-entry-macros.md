---
title: COM 接口入口宏 |Microsoft 文档
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c3ba41a05813c4112c1e5dd51bfe447d2c8debf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366583"
---
# <a name="cominterfaceentry-macros"></a>COM_INTERFACE_ENTRY 宏  
 这些宏在以便其可以访问通过其 COM 映射到输入对象的接口`QueryInterface`。 COM 映射中的项的顺序有顺序接口将检查匹配**IID**期间`QueryInterface`。  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY](#com_interface_entry)|将接口输入到 COM 接口映射。|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|使用此宏来消除歧义的继承的两个分支。|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|使用此宏输入到 COM 映射的接口，并指定其 IID。|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，只是你可以指定不同的 IID。|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 导致转发到查询`punk`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它会自动创建所描述的聚合`clsid`。|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 导致转发到查询`punk`，并且如果`punk`是**NULL**，则自动创建聚合所描述`clsid`。|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|导致你的程序以调用[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)时为查询指定的接口。|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|将每个实例的特定接口的数据的保存。|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|公开分离式接口。|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|当处理到达的 COM 映射中的此项目时，请处理的基类的 COM 映射。|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|有关挂接到 ATL 的一种机制`QueryInterface`逻辑。|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果`func`。|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|返回**E_NOINTERFACE**并终止 COM 映射处理时为查询指定的接口。|  

## <a name="requirements"></a>要求
**标头：** atlcom.h

## <a name="com_interface_entry"></a> COM_INTERFACE_ENTRY
将接口输入到 COM 接口映射。

### <a name="syntax"></a>语法

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>参数

[in] 接口名称的 x 类对象派生自直接。

### <a name="remarks"></a>备注
通常，这是你最常使用的条目类型。

### <a name="example"></a>示例
```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```
### <a name="requirements"></a>要求
**标头：** atlcom.h
  
##  <a name="com_interface_entry2"></a>  COM_INTERFACE_ENTRY2  
 使用此宏来消除歧义的继承的两个分支。  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]你想要从你的对象公开的接口的名称。  
  
 `x2`  
 [in]从其继承分支的名称*x*公开。  
  
### <a name="remarks"></a>备注  
 例如，如果派生类对象从两个双重接口，则公开`IDispatch`使用`COM_INTERFACE_ENTRY2`由于`IDispatch`可以从任一接口获取。  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>  COM_INTERFACE_ENTRY_IID  
 使用此宏输入到 COM 映射的接口，并指定其 IID。  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]公开的接口的 GUID。  
  
 *x*  
 [in]将作为由标识的接口公开其 vtable 类的名称`iid`。  
  
 
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>  COM_INTERFACE_ENTRY2_IID  
 与相同[COM_INTERFACE_ENTRY2](#com_interface_entry2)，只是你可以指定不同的 IID。  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]在指定的接口的 GUID。  
  
 *x*  
 [in]类对象直接派生自接口的名称。  
  
 `x2`  
 [in]直接派生自类对象的第二个接口的名称。  
  
##  <a name="com_interface_entry_aggregate"></a>  COM_INTERFACE_ENTRY_AGGREGATE  
 接口由`iid`，查询`COM_INTERFACE_ENTRY_AGGREGATE`将转发到`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 `punk`假定参数是指向未知的内部对象的聚合或**NULL**，在这种情况下条目被忽略。 通常情况下，将**可以共同创建**中的聚合`FinalConstruct`。  
  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>  COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，只不过查询任何 IID 导致转发到查询`punk`。  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>参数  
 `punk`  
 [in]名称**IUnknown**指针。  
  
### <a name="remarks"></a>备注  
 如果接口查询失败，将继续处理 COM 映射。  
  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 与相同[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)，除非`punk`是**NULL**，它会自动创建所描述的聚合`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]查询接口的 GUID。  
  
 `punk`  
 [in]名称**IUnknown**指针。 必须是包含 COM 映射的类成员。  
  
 `clsid`  
 [in]如果将创建聚合的标识符`punk`是**NULL**。  
  
### <a name="remarks"></a>备注  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>  COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 与相同[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)，只不过查询任何 IID 导致转发到查询`punk`，并且如果`punk`是**NULL**，则自动创建聚合所描述`clsid`。  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>参数  
 `punk`  
 [in]名称**IUnknown**指针。 必须是包含 COM 映射的类成员。  
  
 `clsid`  
 [in]如果将创建聚合的标识符`punk`是**NULL**。  
  
### <a name="remarks"></a>备注  
 如果接口查询失败，将继续处理 COM 映射。  
  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>  COM_INTERFACE_ENTRY_BREAK  
 导致你的程序以调用[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297)时为查询指定的接口。  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]用于构造的接口标识符的文本。  
  
### <a name="remarks"></a>备注  
 将通过附加构造 IID 接口*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>  COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 将每个实例的特定接口的数据的保存。  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]分离式接口的 GUID。  
  
 *x*  
 [in]实现接口的类的名称。  
  
 `punk`  
 [in]名称**IUnknown**指针。 必须是包含 COM 映射的类成员。 应初始化为**NULL**类对象的构造函数中。  
  
### <a name="remarks"></a>备注  
 如果未使用该接口，这会降低你的对象的总体实例大小。  
  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>  COM_INTERFACE_ENTRY_TEAR_OFF  
 公开分离式接口。  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]分离式接口的 GUID。  
  
 *x*  
 [in]实现接口的类的名称。  
  
### <a name="remarks"></a>备注  
 分离式接口被实现为查询每次该接口表示实例化一个单独的对象。 通常情况下，生成你的接口作为拖曳如果极少数情况下使用该接口，因为这可节省主要对象的每个实例的 vtable 指针。 分离式就会删除其引用计数变为零。 分离式实现的类应派生自`CComTearOffObjectBase`和具有其自己的 COM 代码图。  
  
  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>  COM_INTERFACE_ENTRY_CHAIN  
 当处理到达的 COM 映射中的此项目时，请处理的基类的 COM 映射。  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>参数  
 classname  
 [in]当前对象的基类。  
  
### <a name="remarks"></a>备注  
 例如，在以下代码：  
  
 [!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 请注意，COM 映射中的第一个输入必须是包含 COM 映射的对象上的接口。 因此，无法启动与你 COM 映射项`COM_INTERFACE_ENTRY_CHAIN`，这将导致产生不同的对象要搜索的点处的 COM 映射其中**COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** 将显示在对象的 COM 映射。 如果你想要搜索的另一个对象的 COM 映射首先，添加为一个接口条目**IUnknown**到 COM 图中，然后链接其他对象的 COM 映射。 例如：  
  
 [!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>  COM_INTERFACE_ENTRY_FUNC  
 有关挂接到 ATL 的一种机制`QueryInterface`逻辑。  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]公开的接口的 GUID。  
  
 `dw`  
 [in]参数传递给`func`。  
  
 `func`  
 [in]将返回的函数指针`iid`。  
  
### <a name="remarks"></a>备注  
 如果*iid*匹配查询，该接口然后由指定的函数的 IID`func`调用。 该函数的声明应为：  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 当你的函数调用`pv`指向类对象。 `riid`参数是指要查询，该接口`ppv`是一个指针指向该函数应在其中存储的接口指针的位置和`dw`是条目中指定的参数。 该函数应设置\*`ppv`到**NULL**并返回**E_NOINTERFACE**或**S_FALSE**如果它选择不返回一个接口。 与**E_NOINTERFACE**，COM 映射处理终止。 与**S_FALSE**，COM 映射处理继续进行，即使返回没有接口指针。 如果该函数将返回的接口指针，它应返回`S_OK`。  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>  COM_INTERFACE_ENTRY_FUNC_BLIND  
 与相同[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)，只不过对的调用中查询任何 IID 结果`func`。  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>参数  
 `dw`  
 [in]参数传递给`func`。  
  
 `func`  
 [in]获取处理 COM 映射中的此项时调用的函数。  
  
### <a name="remarks"></a>备注  
 任何失败将导致处理在 COM 映射上继续。 如果该函数将返回的接口指针，它应返回`S_OK`。  
  
  
##  <a name="com_interface_entry_nointerface"></a>  COM_INTERFACE_ENTRY_NOINTERFACE  
 返回**E_NOINTERFACE**并终止 COM 映射处理时为查询指定的接口。  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]用于构造的接口标识符的文本。  
  
### <a name="remarks"></a>备注  
 可以使用此宏以防止在特定用例中使用的接口。 例如，可以将此宏插入您的 COM 映射前`COM_INTERFACE_ENTRY_AGGREGATE_BLIND`以防止接口查询转发到聚合的内部未知。  
  
 将通过附加构造 IID 接口*x*到`IID_`。 例如，如果*x*是`IPersistStorage`，将 IID `IID_IPersistStorage`。  
  
  