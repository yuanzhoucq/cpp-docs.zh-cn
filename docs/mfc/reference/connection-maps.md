---
title: "连接映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8947930d20cc65075abe442b233e4c086f10f76e
ms.lasthandoff: 02/24/2017

---
# <a name="connection-maps"></a>连接映射
OLE 控件都能够公开的接口连接到其他应用程序。 这些接口只在该控件允许从容器的访问。 如果 OLE 控件想要访问的其他 OLE 对象的外部接口，必须建立的连接点。 此连接点允许传出外部调度映射，如事件映射或通知函数的访问控制。  
  
 Microsoft 基础类库提供了一个编程模型，支持连接点。 在此模型中，"连接映射"用于指定接口或 OLE 控件的连接点。 连接映射包含每个连接点的一个宏。 连接映射的详细信息，请参阅[CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md)类。  
  
 通常情况下，控件将支持只是两个连接点︰ 一个用于事件，另一个用于属性通知。 这些功能通过实现`COleControl`和需要任何额外工作由控件编写器的基类。 必须手动添加您想要在您的类中实现的任何其他连接点。 若要支持连接映射和点，MFC 提供了下列宏︰  
  
### <a name="connection-map-declaration-and-demarcation"></a>连接映射声明和划分  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|声明的嵌入的类中实现 （必须在类声明中使用） 的其他连接点。|  
|[END_CONNECTION_PART](#end_connection_part)|结束连接点 （必须在类声明中使用） 的声明。|  
|[CONNECTION_IID](#connection_iid)|指定控件的连接点的接口 ID。|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|声明连接映射，将使用的类 （必须在类声明中使用） 中。|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|开始连接映射 （必须在类实现中使用） 的定义。|  
|[END_CONNECTION_MAP](#end_connection_map)|结束连接映射 （必须在类实现中使用） 的定义。|  
|[CONNECTION_PART](#connection_part)|在控件的连接映射中指定的连接点。|  
  
 以下函数帮助中的接收器建立和断开连接使用连接点︰  
  
### <a name="initializationtermination-of-connection-points"></a>初始化/终止的连接点  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|建立源和接收器之间的连接。|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|将一个源和接收器之间的连接中断。|  
  
##  <a name="a-namebeginconnectionparta--beginconnectionpart"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART  
 使用`BEGIN_CONNECTION_PART`从开始进行额外的连接点的事件和属性的通知连接点超出定义的宏。  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定它的连接点这样的控件类的名称。  
  
 *localClass*  
 指定实现连接点的局部类的名称。  
  
### <a name="remarks"></a>备注  
 在定义您的类的成员函数声明 (.h) 文件中，启动的连接点`BEGIN_CONNECTION_PART`宏，然后添加`CONNECTION_IID`宏，并想要实现，并完成连接点映射与任何其他成员函数`END_CONNECTION_PART`宏。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameendconnectionparta--endconnectionpart"></a><a name="end_connection_part"></a>END_CONNECTION_PART  
 结束连接点的声明。  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>参数  
 *localClass*  
 指定实现连接点的局部类的名称。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameconnectioniida--connectioniid"></a><a name="connection_iid"></a>CONNECTION_IID  
 在 `BEGIN_CONNECTION_PART` 和 `END_CONNECTION_PART` 宏之间使用以定义 OLE 控件支持的连接点的接口 ID。  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 接口的接口 ID 由连接点调用。  
  
### <a name="remarks"></a>备注  
 `iid` 参数是一个接口 ID，用于标识连接点在其连接的接收器中调用的接口。 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints #&10;](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 指定调用 `ISinkInterface` 接口的连接点。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-namedeclareconnectionmapa--declareconnectionmap"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP  
 程序中的每个 `COleControl` 派生类可提供一个连接映射来指定控件支持的额外的连接点。  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>备注  
 如果控件支持额外的点，请在类声明的末尾使用 `DECLARE_CONNECTION_MAP` 宏。 然后，在定义类的成员函数的 .cpp 文件中，使用 `BEGIN_CONNECTION_MAP` 宏、控件的每个连接点的 `CONNECTION_PART` 宏和 `END_CONNECTION_MAP` 宏声明连接映射的结尾。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-namebeginconnectionmapa--beginconnectionmap"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP  
 程序中的每个 `COleControl` 派生类均可提供连接映射来指定控件将支持的连接点。  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定连接映射所属的控件类的名称。  
  
 *theBase*  
 指定 `theClass` 的基类的名称。  
  
### <a name="remarks"></a>备注  
 在实现 (。定义您的类的成员函数的 CPP) 文件启动连接映射与`BEGIN_CONNECTION_MAP`宏，然后为每个使用连接点添加宏条目[CONNECTION_PART](#connection_part)宏。 最后，完成连接映射与[END_CONNECTION_MAP](#end_connection_map)宏。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameendconnectionmapa--endconnectionmap"></a><a name="end_connection_map"></a>END_CONNECTION_MAP  
 结束连接映射的定义。  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameconnectionparta--connectionpart"></a><a name="connection_part"></a>CONNECTION_PART  
 将您的 OLE 控件的连接点映射到一个特定的接口 id。  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定它的连接点这样的控件类的名称。  
  
 `iid`  
 接口的接口 ID 由连接点调用。  
  
 *localClass*  
 指定实现连接点的局部类的名称。  
  
### <a name="remarks"></a>备注  
 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints #&2;](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 实现连接映射，与连接点，调用`IID_ISinkInterface`接口。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameafxconnectionadvisea--afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise  
 调用此函数可由指定的源之间建立连接`pUnkSrc`，和一个水池，由指定`pUnkSink`。  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>参数  
 `pUnkSrc`  
 指向调用接口的对象的指针。  
  
 `pUnkSink`  
 指向实现该接口的对象的指针。  
  
 `iid`  
 连接的接口 ID。  
  
 `bRefCount`  
 **TRUE**指示创建连接应导致的引用计数的`pUnkSink`要递增。 **FALSE**指示不应递增引用计数。  
  
 `pdwCookie`  
 一个指向`DWORD`连接标识符的返回位置。 此值应作为传递`dwCookie`参数`AfxConnectionUnadvise`断开连接时。  
  
### <a name="return-value"></a>返回值  
 非零，如果已建立连接;否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCConnectionPoints #&8;](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>要求  
 **标头︰** afxctl.h 

##  <a name="a-nameafxconnectionunadvisea--afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise  
 调用此函数可断开连接之间由指定的源的连接`pUnkSrc`，和一个水池，由指定`pUnkSink`。  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>参数  
 `pUnkSrc`  
 指向调用接口的对象的指针。  
  
 `pUnkSink`  
 指向实现该接口的对象的指针。  
  
 `iid`  
 连接点接口的接口 ID。  
  
 `bRefCount`  
 **TRUE**指示断开连接的连接应导致的引用计数的`pUnkSink`要递减。 **FALSE**指示不应递减引用计数。  
  
 `dwCookie`  
 返回的连接标识符`AfxConnectionAdvise`。  
  
### <a name="return-value"></a>返回值  
 非零，如果连接已断开连接;否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCConnectionPoints #&9;](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>要求  
 **标头︰** afxctl.h 

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

