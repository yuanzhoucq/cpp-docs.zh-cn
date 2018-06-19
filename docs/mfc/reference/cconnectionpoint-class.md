---
title: CConnectionPoint 类 |Microsoft 文档
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
ms.openlocfilehash: 22793706a67a3d301f88700ca6b43fb9c83e4dc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357385"
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
|[CConnectionPoint::GetConnections](#getconnections)|检索一个连接映射中的所有连接点。|  
|[CConnectionPoint::GetContainer](#getcontainer)|检索拥有连接映射的控件的容器。|  
|[CConnectionPoint::GetIID](#getiid)|检索连接点的接口 ID。|  
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|检索由控件支持的连接点的最大数目。|  
|[在](#getnextconnection)|检索指向处的连接元素的`pos`。|  
|[CConnectionPoint::GetStartPosition](#getstartposition)|通过返回启动映射迭代**位置**值，可以传递给`GetNextConnection`调用。|  
|[CConnectionPoint::OnAdvise](#onadvise)|由框架建立或断开连接时调用。|  
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|检索指向所请求的接收器接口指针。|  
  
## <a name="remarks"></a>备注  
 不同于普通的 OLE 接口，用于实现和公开 OLE 控件的功能，连接点可实现能够对其他对象，如触发事件初始化操作和更改通知的传出接口。  
  
 连接两个部分组成： 调用调用"源"，并实现该接口的对象的接口的对象调用了"接收器。" 通过公开连接点，源允许建立到其自身的连接的接收器。 通过连接点机制，源对象获取指向接收器的实现的一组的成员函数的指针。 例如，若要激发事件接收器实现的源可以调用接收器的实现的适当方法。  
  
 默认情况下， `COleControl`-派生的类实现两个连接点： 一个事件，一个用于属性更改通知。 使用这些连接，分别为事件激发和通知接收器 （例如，控件的容器），当属性值已更改。 OLE 控件以实现额外的连接点的情况下，还提供支持。 对于每个控件类中实现的其他连接点，您必须声明实现连接点的"连接部分"。 如果你实现一个或多个连接点，你还需要声明一个在你的控件类中的"连接映射"。  
  
 下面的示例演示一个简单的连接映射和一个连接点`Sample`包含的代码的两个片段的 OLE 控件： 第一个部分声明连接映射和点; 第二个实现此映射和点。 第一个片段下插入到控件类中，声明`protected`部分：  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]  
  
 `BEGIN_CONNECTION_PART`和`END_CONNECTION_PART`宏声明一个嵌入的类、 `XSampleConnPt` (派生自`CConnectionPoint`) 实现此特定连接点。 如果你想要重写任何`CConnectionPoint`成员函数，或添加你自己的成员函数，将它们声明这些两个宏之间。 例如，`CONNECTION_IID`宏重写`CConnectionPoint::GetIID`成员函数时置于这些两个宏之间。  
  
 第二个代码段插入到实现文件 (。CPP) 的控件类。 此代码实现连接映射，其中包括其他连接点， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]  
  
 一旦已插入这些代码片段，示例 OLE 控件可公开的连接点**ISampleSink**接口。  
  
 通常情况下，连接点支持"多播"，是能够广播到多个连接到相同的接口的接收器。 下面的代码段演示如何通过循环访问每个接收器连接点上完成多播：  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
 此示例检索当前的一组连接上`SampleConnPt`连接点通过调用`CConnectionPoint::GetConnections`。 然后，循环访问的连接和调用`ISampleSink::SinkFunc`上每个活动连接。  
  
 有关详细信息使用`CConnectionPoint`，请参阅文章[连接点](../../mfc/connection-points.md)。  
  
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
 调用此函数可检索连接点的所有活动连接。  
  
```  
const CPtrArray* GetConnections();
```  
  
### <a name="return-value"></a>返回值  
 指向数组的活动连接 （接收器） 的指针。 某些数组中的指针可能是 NULL。 此数组中的每个非 NULL 指针可以安全地转换为指向使用转换运算符的接收器接口的指针。  
  
##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer  
 由框架检索调用**IConnectionPointContainer**连接点。  
  
```  
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，到容器; 的指针否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此函数通常由实现`BEGIN_CONNECTION_PART`宏。  
  
##  <a name="getiid"></a>  CConnectionPoint::GetIID  
 由框架调用以检索连接点的接口 ID。  
  
```  
virtual REFIID GetIID() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 参考连接点的接口 id。  
  
### <a name="remarks"></a>备注  
 重写此函数可返回用于此连接点的接口 ID。  
  
##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections  
 由框架调用以检索最大连接点支持的连接数。  
  
```  
virtual int GetMaxConnections();
```  
  
### <a name="return-value"></a>返回值  
 最大受该控件，则为-1，如果没有限制的连接数。  
  
### <a name="remarks"></a>备注  
 默认实现返回为-1，表示没有限制。  
  
 如果你想要限制可以连接到你的控件的接收器数，重写此函数。  
  
##  <a name="getnextconnection"></a>  在  
 检索指向处的连接元素的`pos`。  
  
```  
LPUNKNOWN GetNextConnection(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 指定对引用**位置**通过前一个返回值`GetNextConnection`或[GetStartPosition](#getstartposition)调用。  
  
### <a name="return-value"></a>返回值  
 指向指定的连接元素的指针`pos`，则为 NULL。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于循环访问连接映射中的所有元素。 当循环时，跳过此函数返回 null 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition  
 通过返回启动映射迭代**位置**值，可以传递给[GetNextConnection](#getnextconnection)调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**值，该值指示来循环映射; 的起始位置或**NULL**如果映射为空。  
  
### <a name="remarks"></a>备注  
 迭代序列是不可预测的;因此，"映射中的第一个元素"必须没有特别的意义。  
  
### <a name="example"></a>示例  
  请参阅示例[在](#getnextconnection)。  
  
##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise  
 由框架在连接时调用是正在建立或破坏。  
  
```  
virtual void OnAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>参数  
 `bAdvise`  
 **TRUE**，如果连接正在建立; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。  
  
 如果你想要通知接收器连接到或断开连接点时，重写此函数。  
  
##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface  
 检索指向所请求的接收器接口指针。  
  
```  
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,  
    void** ppInterface);
```  
  
### <a name="parameters"></a>参数  
 `pUnkSink`  
 所请求的接收器接口的标识符。  
  
 `ppInterface`  
 指向由标识的接口指针的指针`pUnkSink`。 如果对象不支持此接口， \* `ppInterface`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

