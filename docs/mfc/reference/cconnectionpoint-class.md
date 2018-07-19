---
title: CConnectionPoint 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
dev_langs:
- C++
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b092c6a097d39c3114193c578bc37c179ca0df7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336194"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint 类
定义用于与其他 OLE 对象通信的接口（称为“连接点”）的特殊类型。  
  
## <a name="syntax"></a>语法  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|构造 `CConnectionPoint` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CConnectionPoint::GetConnections](#getconnections)|检索连接映射中的所有连接点。|  
|[CConnectionPoint::GetContainer](#getcontainer)|检索拥有连接映射的控件的容器。|  
|[CConnectionPoint::GetIID](#getiid)|检索连接点的接口 ID。|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|检索由控件支持的连接点的最大数目。|  
|[在](#getnextconnection)|检索到的连接元素的指针*pos*。|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|通过返回位置值，可传递给启动映射迭代`GetNextConnection`调用。|  
|[CConnectionPoint::OnAdvise](#onadvise)|由框架建立或断开连接时调用。|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|检索指向请求的接收器接口的指针。|  
  
## <a name="remarks"></a>备注  
 不同于普通的 OLE 接口，可用来实现，并公开 OLE 控件的功能，连接点可实现可以启动对其他对象，如触发事件的操作并更改通知的传出接口。  
  
 连接两个部分组成： 调用名为"源"，并实现接口，该对象的接口的对象称为"接收器"。 通过公开连接点，源允许接收器来建立到其自身的连接。 通过连接点机制，源对象获取指向接收器实现的一组的成员函数的指针。 例如，若要激发事件接收器实现的源可以调用的接收器的实现适当的方法。  
  
 默认情况下，`COleControl`的派生的类实现两个连接点： 一个事件，一个用于属性更改通知。 使用这些连接，分别为事件激发和时通知接收器 （例如，控件的容器） 属性值已更改。 OLE 控件以实现额外的连接点的情况下，还提供支持。 对于每个控件类中实现附加的连接点，您必须声明"连接部分"实现连接点。 如果你实现一个或多个连接点，还需要声明一个控件类中的"连接映射"。  
  
 下面的示例演示一个简单的连接映射和一个连接点`Sample`包含的代码的两个片段的 OLE 控件： 第一个部分声明连接映射和点; 第二个实现此映射和点。 第一个片段下插入到控件类的声明**保护**部分：  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 BEGIN_CONNECTION_PART 和 END_CONNECTION_PART 宏声明嵌入的类， `XSampleConnPt` (派生自`CConnectionPoint`) 实现此特定连接点。 如果你想要重写任何`CConnectionPoint`成员函数，或添加您自己的成员函数，将它们声明两个两个宏之间。 例如，CONNECTION_IID 宏重写`CConnectionPoint::GetIID`成员函数时放置在以下两个宏之间。  
  
 第二个代码片段插入到实现文件 (。CPP) 的控件类。 该代码将实现连接映射，其中包括附加的连接点， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 一旦已插入这些代码片段，该示例 OLE 控件公开的连接点`ISampleSink`接口。  
  
 通常情况下，连接点支持"多播"，是能够广播到多个接收器连接到相同的接口。 下面的代码段演示了如何通过循环访问连接点上的每个接收器完成多播：  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 此示例检索当前的连接集上`SampleConnPt`连接点通过调用`CConnectionPoint::GetConnections`。 然后循环访问连接和调用`ISampleSink::SinkFunc`上每个活动连接。  
  
 有关使用的详细信息`CConnectionPoint`，请参阅文章[连接点](../../mfc/connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint  
 构造 `CConnectionPoint` 对象。  
  
```  
CConnectionPoint();
```  
  
##  <a name="getconnections"></a>  CConnectionPoint::GetConnections  
 调用此函数可检索的连接点的所有活动连接。  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>返回值  
 指向数组的活动连接 （接收器） 的指针。 指针在数组中的一些可能为 NULL。 此数组中的每个非 NULL 指针可以安全地转换为指向使用转换运算符的接收器接口的指针。  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 由框架调用以检索`IConnectionPointContainer`连接点。  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，指向容器;否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 此函数通常是由 BEGIN_CONNECTION_PART 宏实现的。  
  
##  <a name="getiid"></a>  CConnectionPoint::GetIID  
 由框架调用以检索连接点的接口 ID。  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 对连接点的接口 id。  
  
### <a name="remarks"></a>备注  
 重写此函数可返回用于此连接点的接口 ID。  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 由框架调用以检索的最大受支持的连接点的连接数。  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>返回值  
 最大受支持的控件，则为-1，如果没有限制连接数。  
  
### <a name="remarks"></a>备注  
 默认实现返回-1，表示无限制。  
  
 如果你想要限制可以连接到您的控件的接收器的数目来覆盖此函数。  
  
##  <a name="getnextconnection"></a>  在  
 检索到的连接元素的指针*pos*。  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 *pos*  
 指定对先前返回的位置值的引用`GetNextConnection`或[GetStartPosition](#getstartposition)调用。  
  
### <a name="return-value"></a>返回值  
 指向由指定的连接元素的指针*pos*，或为 NULL。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于通过连接映射中的所有元素。 在迭代过程中，请跳过此函数返回的任何 null 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 通过返回位置值，可传递给启动映射迭代[GetNextConnection](#getnextconnection)调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 位置值，该值指示用于循环访问映射的起始位置或者，如果映射为空，则为 NULL。  
  
### <a name="remarks"></a>备注  
 迭代序列不是可预测;因此，"映射中的第一个元素"有没有特别的意义。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[在](#getnextconnection)。  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 连接时由框架调用是建立或断开。  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>参数  
 *bAdvise*  
 正在建立的连接; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。  
  
 如果希望通知接收器连接到或断开连接点时，重写此函数。  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 检索指向请求的接收器接口的指针。  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>参数  
 *pUnkSink*  
 所请求的接收器接口的标识符。  
  
 *ppInterface*  
 通过标识的接口指针的指针*pUnkSink*。 如果该对象不支持此接口， \* *ppInterface*设置为 NULL。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

