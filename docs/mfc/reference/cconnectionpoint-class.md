---
title: "CConnectionPoint 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- CConnectionPoint class
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a511f252bf921433d070059518e6e67b952680eb
ms.lasthandoff: 02/24/2017

---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 类
定义用于与其他 OLE 对象通信的接口（称为“连接点”）的特殊类型。  
  
## <a name="syntax"></a>语法  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|构造 `CConnectionPoint` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CConnectionPoint::GetConnections](#getconnections)|检索一个连接映射中的所有连接点。|  
|[CConnectionPoint::GetContainer](#getcontainer)|检索拥有连接映射的控件的容器。|  
|[CConnectionPoint::GetIID](#getiid)|检索连接点的接口 ID。|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|检索控件支持的连接点的最大数目。|  
|[在](#getnextconnection)|检索指向处的连接元素的指针`pos`。|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|通过返回启动映射迭代**位置**值，可以传递给`GetNextConnection`调用。|  
|[CConnectionPoint::OnAdvise](#onadvise)|由框架建立或断开连接时调用。|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|检索指向请求的接收器接口的指针。|  
  
## <a name="remarks"></a>备注  
 与普通的 OLE 接口，用于实现和公开 OLE 控件的功能，不同的连接点实现了可以启动对其他对象，如触发事件的操作和更改通知的传出接口。  
  
 连接由两部分组成︰ 调用该接口，称为"源"，并实现接口，该对象的对象称为"接收器"。 通过公开连接点，则 source 允许接收器，以建立与自身连接。 连接点机制，通过源对象获取对该接收器实现的一组的成员函数的指针。 例如，若要激发事件接收器实现的源可以调用该接收器实现的适当方法。  
  
 默认情况下，`COleControl`的派生的类实现两个连接点︰ 一个事件，一个用于属性更改通知。 使用这些连接，分别为事件触发和通知接收器 （例如，控件的容器） 当属性值已更改。 OLE 控件以实现额外的连接点还提供支持。 对于每个控件类中实现附加的连接点，您必须声明实现连接点的"连接部分"。 如果实现一个或多个连接点，您还需要声明一个在控件类中的"连接映射"。  
  
 下面的示例演示一个简单的连接映射和为一个连接点`Sample`包含的代码的两个片段的 OLE 控件︰ 的第一部分声明连接映射和点; 第二个实现此映射和点。 第一个片段插入到的控件类中，声明下`protected`部分︰  
  
 [!code-cpp[NVC_MFCConnectionPoints #&7;](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 `BEGIN_CONNECTION_PART`和`END_CONNECTION_PART`宏声明嵌入的类， `XSampleConnPt` (派生自`CConnectionPoint`) 实现此特定连接点。 如果您想要重写任何`CConnectionPoint`成员函数，或添加您自己的成员函数，将它们声明这两种宏之间。 例如，`CONNECTION_IID`宏重写`CConnectionPoint::GetIID`成员函数时放置在这两种宏之间。  
  
 第二个代码段插入到实现文件 (。CPP) 的控件类。 此代码实现连接映射，包括附加的连接点， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints #&2;](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 一旦已插入的这些代码片段，示例 OLE 控件都公开的连接点**ISampleSink**接口。  
  
 通常情况下，连接点支持"多播"，是指广播到多个连接到同一接口的接收器的能力。 下面的代码段演示如何通过循环访问每个连接点上的接收器实现多播︰  
  
 [!code-cpp[NVC_MFCConnectionPoints #&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 此示例检索当前的一组连接上`SampleConnPt`连接点，通过调用`CConnectionPoint::GetConnections`。 然后，循环访问该连接并调用`ISampleSink::SinkFunc`上每个活动连接。  
  
 有关详细信息使用`CConnectionPoint`，请参阅文章[连接点](../../mfc/connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="a-namecconnectionpointa--cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint  
 构造 `CConnectionPoint` 对象。  
  
```  
CConnectionPoint();
```  
  
##  <a name="a-namegetconnectionsa--cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections  
 调用此函数可检索所有活动连接的连接点。  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>返回值  
 指向活动连接 （接收器） 的数组的指针。 某些中数组的指针可能是 NULL。 此数组中的每个非 NULL 指针可以安全地转换为指向使用强制转换运算符的接收器接口的指针。  
  
##  <a name="a-namegetcontainera--cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer  
 由框架调用以检索**IConnectionPointContainer**连接点。  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，到容器; 的指针否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数通常由实现`BEGIN_CONNECTION_PART`宏。  
  
##  <a name="a-namegetiida--cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID  
 由框架来检索连接点的接口 ID 调用。  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 参考连接点的接口 id。  
  
### <a name="remarks"></a>备注  
 重写此函数可返回用于此连接点的接口 ID。  
  
##  <a name="a-namegetmaxconnectionsa--cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections  
 由要检索的最大连接点所支持的连接数的框架调用。  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>返回值  
 最大受该控件，则为-1，如果没有限制的连接数。  
  
### <a name="remarks"></a>备注  
 默认实现将返回-1，表示无限制。  
  
 如果您想要限制可以连接到您的控件的接收器的数目，重写此函数。  
  
##  <a name="a-namegetnextconnectiona--cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>在  
 检索指向处的连接元素的指针`pos`。  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 指定对引用**位置**返回先前值`GetNextConnection`或[GetStartPosition](#getstartposition)调用。  
  
### <a name="return-value"></a>返回值  
 指向由指定的连接元素的指针`pos`，则为 NULL。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于循环访问连接映射中的所有元素。 当循环时，跳过从该函数返回的任何 null 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCConnectionPoints #&4;](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="a-namegetstartpositiona--cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition  
 通过返回启动映射迭代**位置**值，可以传递给[GetNextConnection](#getnextconnection)调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，该值指示为循环映射; 的起始位置或**NULL**如果映射为空。  
  
### <a name="remarks"></a>备注  
 迭代序列是不可预测的;因此，"在映射中的第一个元素"有没有特别的意义。  
  
### <a name="example"></a>示例  
  请参阅示例[在](#getnextconnection)。  
  
##  <a name="a-nameonadvisea--cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise  
 由框架的连接时调用是建立或断开。  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 **TRUE**，如果连接正在建立; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。  
  
 如果您想要通知接收器连接到或从连接点断开连接时，重写此函数。  
  
##  <a name="a-namequerysinkinterfacea--cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface  
 检索指向请求的接收器接口的指针。  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>参数  
 `pUnkSink`  
 正在请求的接收器接口的标识符。  
  
 `ppInterface`  
 指向由标识的接口指针的指针`pUnkSink`。 如果该对象不支持此接口， \* `ppInterface`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


