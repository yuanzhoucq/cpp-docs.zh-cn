---
title: CAnimationBaseObject 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 135bb279daf4c000c025ac6f8fa51a6b023e2d1e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952539"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 类
所有动画对象的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|已重载。 将构造一个动画对象。|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|析构函数。 当动画对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|将添加到情节提要与封装的动画变量的转换。|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|删除所有相关的转换。|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|确定的动画对象是否包含特定动画变量。|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|创建关联的动画对象的转换。|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|分离父动画控制器中的动画对象。|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|设置整数值已更改事件处理程序。|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|设置值发生更改时事件处理程序。|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|指示是否自动销毁相关的转换。|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|返回当前的组 id。|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|返回当前对象 id。|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|返回用户定义数据。|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|设置用于自动销毁转换进行排序的标志。|  
|[CAnimationBaseObject::SetID](#setid)|设置新的 Id。|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|设置用户定义的数据。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|收集到包含的动画变量的指针。|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|动画对象与它们的容器中包含的动画变量之间建立关系。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应自动销毁相关的转换。|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|将用户定义数据存储。|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|指定的动画对象的组 ID。|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|指定动画对象的对象 ID。|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|指向父动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 此类实现所有动画对象的基本方法。 动画对象可以表示值、 点、 大小、 矩形或颜色在应用程序，以及任何自定义的实体。 动画对象存储在动画组 （请参阅 CAnimationGroup）。 每个组可以单独动画处理，并且可以被视为情节提要的相似之处。 动画对象所封装一个或多个动画变量 （请参阅 CAnimationVariable），具体取决于其逻辑表示形式。 例如，CAnimationRect 包含四个动画变量的每个边的矩形的一个变量。 每个动画对象类公开重载的 AddTransition 方法，该应该用于将转换应用到封装的动画变量的方法。 动画对象可以识别通过对象 ID （可选） 和组 id。 组 ID 是必需的才能放置到正确的组的动画对象，但如果未指定组 ID，将对象放置在具有 ID 0 的默认组。 如果调用使用不同的 GroupID SetID，动画对象将移到另一个组 （如有必要，正在创建新的组） 中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject  
 析构函数。 当动画对象被销毁时调用。  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions  
 将添加到情节提要与封装的动画变量的转换。  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>参数  
 *pStoryboard*  
 指向情节提要的指针。  
  
 *bDependOnKeyframes*  
 为 false，则此方法将添加仅这些不依赖于关键帧的转换。  
  
### <a name="return-value"></a>返回值  
 如果已成功添加转换，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 添加已添加了 AddTransition （派生类中的重载方法），到情节提要的相关的转换。  
  
##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject  
 将构造一个动画对象。  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 *nGroupID*  
 指定组 id。  
  
 *nObjectID*  
 指定对象 id。  
  
 *dwUserData*  
 用户定义数据，它可以与动画对象相关联并在运行时检索更高版本。  
  
### <a name="remarks"></a>备注  
 构造动画对象，并分配默认对象 ID (0) 和组 ID (0)。  
  
##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions  
 删除所有相关的转换。  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>参数  
 *bAutodestroy*  
 指定是否自动销毁转换对象或只需从相关列表中删除它们。  
  
### <a name="remarks"></a>备注  
 删除所有相关的转换并销毁它们 bAutodestroy 或 m_bAutodestroyTransitions 标志为 TRUE。 仅当它们不堆栈上分配，转换应自动销毁。 如果以上标志为 FALSE，转换只会从相关的转换的内部列表。  
  
##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable  
 确定的动画对象是否包含特定动画变量。  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>参数  
 *pVariable*  
 指向动画变量的指针。  
  
### <a name="return-value"></a>返回值  
 动画变量包含在动画对象中; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法可以用于确定是否动画对象内包含指定 pVariable 动画变量。 动画对象，具体取决于其类型，可能包含多个动画变量。 例如，CAnimationColor 包含三个变量，一个用于每个颜色组件 （红色、 绿色和蓝色）。 动画变量的值已更改时，Windows 动画 API 发送 ValueChanged 或 IntegerValueChanged 事件 （如果启用），以及此事件的参数是指向接口 IUIAnimationVariable 动画变量的指针。 此方法可帮助从指向包含 COM 对象的指针到动画获取指针。  
  
##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions  
 创建关联的动画对象的转换。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建的已转换，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 循环访问在派生的动画对象中封装的动画变量的列表，并创建与每个动画变量关联的转换。  
  
##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController  
 分离父动画控制器中的动画对象。  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>备注  
 此方法在内部使用。  
  
##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent  
 设置整数值已更改事件处理程序。  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 *pController*  
 指向父控制器的指针。  
  
 *bEnable*  
 指定是否启用或禁用整数值已更改事件。  
  
### <a name="remarks"></a>备注  
 如果启用了整数值已更改事件处理程序，你可以处理此事件在 CAnimationController::OnAnimationIntegerValueChanged 方法中，应在 CAnimationController 派生类中被覆盖。 每次的动画整数值已更改时，调用此方法。  
  
##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent  
 设置值发生更改时事件处理程序。  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 *pController*  
 指向父控制器的指针。  
  
 *bEnable*  
 指定是否启用或禁用值已更改事件。  
  
### <a name="remarks"></a>备注  
 如果启用了值发生更改时事件处理程序，你可以处理此事件在 CAnimationController::OnAnimationValueChanged 方法中，应在 CAnimationController 派生类中被覆盖。 每次的动画值已更改时，调用此方法。  
  
##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList  
 收集到包含的动画变量的指针。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>参数  
 *lst*  
 必须填入动画对象中包含的动画变量的列表。  
  
### <a name="remarks"></a>备注  
 这是必须在派生类中重写的纯虚方法。 动画对象，具体取决于其类型，包含一个或多个动画变量。 例如，CAnimationPoint 包含 X 和 Y 坐标分别表示两个变量。 基类 CAnimationBaseObject 实现某些泛型方法，作用于动画变量的列表： ApplyTransitions、 ClearTransitions、 EnableValueChangedEvent、 EnableIntegerValueChangedEvent。 这些方法调用 GetAnimationVariableList，派生类中使用特定的动画对象中包含的实际动画变量填充，然后循环访问列表并执行必要的操作。 如果创建自定义的动画对象时，你必须向 lst 添加该对象中包含的所有动画变量。  
  
##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions  
 指示是否自动销毁相关的转换。  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，自动; 销毁相关的转换如果为 FALSE，则应通过调用应用程序释放转换对象。  
  
### <a name="remarks"></a>备注  
 默认情况下此标志为 TRUE。 仅当分配堆栈上的转换和/或转换应释放通过调用应用程序，请设置此标志。  
  
##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID  
 返回当前的组 id。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前组 id。  
  
### <a name="remarks"></a>备注  
 使用此方法来检索组 id。 如果组 ID 尚未设置显式构造函数中或与 SetID，它的 0。  
  
##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID  
 返回当前对象 id。  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前对象 id。  
  
### <a name="remarks"></a>备注  
 使用此方法来检索对象 id。 如果对象 ID 尚未设置显式构造函数中或与 SetID，它的 0。  
  
##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData  
 返回用户定义数据。  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>返回值  
 自定义的数据的值。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索自定义数据在运行时。 如果它未显式初始化在构造函数或使用 SetUserData，返回的值将为 0。  
  
##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions  
 指定是否应自动销毁相关的转换。  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData  
 将用户定义数据存储。  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID  
 指定的动画对象的组 ID。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID  
 指定动画对象的对象 ID。  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController  
 指向父动画控制器的指针。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions  
 设置用于自动销毁转换进行排序的标志。  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>参数  
 *bValue*  
 指定自动销毁标志。  
  
### <a name="remarks"></a>备注  
 设置此标志，仅当你分配了使用运算符 new 的转换对象。 如果由于某种原因，在堆栈分配转换对象，自动销毁标志应为 FALSE。 默认情况下此标志为 TRUE。  
  
##  <a name="setid"></a>  CAnimationBaseObject::SetID  
 设置新的 Id。  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>参数  
 *nObjectID*  
 指定新的对象 id。  
  
 *nGroupID*  
 指定新的组 id。  
  
### <a name="remarks"></a>备注  
 允许更改对象 ID 和组 id。 如果新的组 ID 不同于当前的 ID，动画对象移动到另一个组 （新的组将被创建，如有必要）。  
  
##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects  
 动画对象与它们的容器中包含的动画变量之间建立关系。  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>备注  
 这是一个帮助器，可以用于建立一个动画的对象和其容器中包含的动画变量之间的关系。 它循环访问动画变量，并将后向指针设置为每个动画变量将父动画对象。 在当前实现中在 CAnimationBaseObject::ApplyTransitions 中建立的实际关系，因此后指针不会设置直到你调用 CAnimationGroup::Animate。 在你处理事件和需要获取父动画对象 CAnimationVariable （使用 CAnimationVariable::GetParentAnimationObject） 时，知道关系可能会有用。  
  
##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData  
 设置用户定义的数据。  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>参数  
 *dwUserData*  
 指定的自定义数据。  
  
### <a name="remarks"></a>备注  
 使用此方法将自定义数据关联的动画对象。 此数据可能更高版本在运行时通过检索 GetUserData。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
