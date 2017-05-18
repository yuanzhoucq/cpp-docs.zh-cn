---
title: "CAnimationRect 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationRect class
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: f935884301030166572e356fffe88439f843f2c7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="canimationrect-class"></a>CAnimationRect 类
实现可对矩形边进行动画处理的矩形功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](#canimationrect)|已重载。 构造动画 rect 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](#addtransition)|添加的左侧、 顶部、 右侧和底部坐标的转换。|  
|[CAnimationRect::GetBottom](#getbottom)|提供对表示底部坐标 CAnimationVariable 访问。|  
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|返回矩形边界的默认的值。|  
|[CAnimationRect::GetLeft](#getleft)|提供访问权限 CAnimationVariable 表示左的坐标。|  
|[CAnimationRect::GetRight](#getright)|提供对表示右坐标 CAnimationVariable 访问。|  
|[CAnimationRect::GetTop](#gettop)|提供访问权限 CAnimationVariable 表示上坐标。|  
|[CAnimationRect::GetValue](#getvalue)|返回当前值。|  
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|设置默认值。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|将封装的动画变量放入列表。 (重写[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationRect::operator RECT](#operator_rect)|将 CAnimationRect 转换为矩形|  
|[CAnimationRect::operator =](#operator_eq)|将 rect 分配给 CAnimationRect。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|指定矩形是否具有固定大小。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|封装的动画变量，表示底层动画矩形的边界。|  
|[CAnimationRect::m_leftValue](#m_leftvalue)|表示左封装的动画变量的动画矩形边界。|  
|[CAnimationRect::m_rightValue](#m_rightvalue)|表示右封装的动画变量的动画矩形边界。|  
|[CAnimationRect::m_szInitial](#m_szinitial)|指定动画矩形的初始大小。|  
|[CAnimationRect::m_topValue](#m_topvalue)|封装的动画变量表示顶部动画矩形的边界。|  
  
## <a name="remarks"></a>备注  
 CAnimationRect 类封装四个 CAnimationVariable 对象，并可以表示在应用程序中一个矩形。 若要在应用程序中使用此类，只需实例化此类的对象、 将其添加到动画控制器使用 CAnimationController::AddAnimationObject 和调用为每个转换的 AddTransition 要应用于左、 右边缘和下坐标。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationRect`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationRect::AddTransition  
 添加的左侧、 顶部、 右侧和底部坐标的转换。  
  
```  
void AddTransition(
    CBaseTransition* pLeftTransition,  
    CBaseTransition* pTopTransition,  
    CBaseTransition* pRightTransition,  
    CBaseTransition* pBottomTransition);
```  
  
### <a name="parameters"></a>参数  
 `pLeftTransition`  
 指定转换的左侧。  
  
 `pTopTransition`  
 指定转换的顶边。  
  
 `pRightTransition`  
 指定的左右两边的转换。  
  
 `pBottomTransition`  
 指定转换的底边。  
  
### <a name="remarks"></a>备注  
 调用此函数可将指定的转换添加到内部列表应用于每个矩形边的动画变量的转换。 当您添加转换时，它们将不会立即应用并存储在内部列表。 转换将应用 （添加到情节提要为特定值） 当您调用 CAnimationController::AnimateGroup。 如果您不需要将转换应用到一个矩形边，可以传递 NULL。  
  
##  <a name="canimationrect"></a>CAnimationRect::CAnimationRect  
 构造 CAnimationRect 对象。  
  
```  
CAnimationRect();

 
CAnimationRect(
    const CRect& rect,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    const CPoint& pt,  
    const CSize& sz,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    int nLeft,  
    int nTop,  
    int nRight,  
    int nBottom,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 指定默认矩形。  
  
 `nGroupID`  
 指定组的 id。  
  
 `nObjectID`  
 指定的对象 id。  
  
 `dwUserData`  
 指定用户定义的数据。  
  
 `pt`  
 左上角的坐标。  
  
 `sz`  
 矩形的大小。  
  
 `nLeft`  
 指定左边边界的坐标。  
  
 `nTop`  
 指定绑定的顶部的坐标。  
  
 `nRight`  
 指定右边界的坐标。  
  
 `nBottom`  
 指定绑定的底部的坐标。  
  
### <a name="remarks"></a>备注  
 使用默认值为左侧、 顶部、 右侧和底部，对象 ID 和组 ID，将设置为 0 构造的对象。 它们可以在运行时使用 SetDefaultValue SetID 以后更改。  
  
##  <a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList  
 将封装的动画变量放入列表。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>参数  
 `lst`  
 当函数返回时，它包含指向四个 CAnimationVariable 对象，表示矩形的坐标的指针。  
  
##  <a name="getbottom"></a>CAnimationRect::GetBottom  
 提供对表示底部坐标 CAnimationVariable 访问。  
  
```  
CAnimationVariable& GetBottom();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示底部坐标的引用。  
  
### <a name="remarks"></a>备注  
 您可以调用此方法以获取直接访问基础 CAnimationVariable 表示底部坐标。  
  
##  <a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue  
 返回矩形边界的默认的值。  
  
```  
CRect GetDefaultValue();
```  
  
### <a name="return-value"></a>返回值  
 一个包含左、 右、 顶部和底部的默认值的 CRect 值。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索由构造函数或 SetDefaultValue 以前设置的默认值。  
  
##  <a name="getleft"></a>CAnimationRect::GetLeft  
 提供访问权限 CAnimationVariable 表示左的坐标。  
  
```  
CAnimationVariable& GetLeft();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示左的坐标的引用。  
  
### <a name="remarks"></a>备注  
 您可以调用此方法以获取直接访问基础 CAnimationVariable 表示的左的坐标。  
  
##  <a name="getright"></a>CAnimationRect::GetRight  
 提供对表示右坐标 CAnimationVariable 访问。  
  
```  
CAnimationVariable& GetRight();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示右坐标的引用。  
  
### <a name="remarks"></a>备注  
 您可以调用此方法以获取直接访问基础 CAnimationVariable 表示右坐标。  
  
##  <a name="gettop"></a>CAnimationRect::GetTop  
 提供访问权限 CAnimationVariable 表示上坐标。  
  
```  
CAnimationVariable& GetTop();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示上坐标的引用。  
  
### <a name="remarks"></a>备注  
 您可以调用此方法以获取直接访问基础 CAnimationVariable 表示的上坐标。  
  
##  <a name="getvalue"></a>CAnimationRect::GetValue  
 返回当前值。  
  
```  
BOOL GetValue(CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 输出。 此方法返回时包含的当前值。  
  
### <a name="return-value"></a>返回值  
 已成功检索的当前值; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索当前动画矩形的值。 如果此方法失败或基础 COM 对象左侧、 顶部、 右侧和底部对尚未初始化，rect 包含构造函数中或通过 SetDefaultValue 以前设置的默认值。  
  
##  <a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize  
 指定矩形是否具有固定大小。  
  
```  
BOOL m_bFixedSize;  
```  
  
### <a name="remarks"></a>备注  
 如果此成员为 true，然后矩形的大小是固定和向右和探底值每的次重新计算的左上角移动根据固定大小。 将此值设置为 TRUE 以轻松地移动屏幕周围的矩形。 在这种情况下应用于右边和底边坐标的转换将被忽略。 当构造对象和/或调用 SetDefaultValue 内部存储大小。 默认情况下此成员设置为 FALSE。  
  
##  <a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue  
 封装的动画变量，表示底层动画矩形的边界。  
  
```  
CAnimationVariable m_bottomValue;  
```  
  
##  <a name="m_leftvalue"></a>CAnimationRect::m_leftValue  
 表示左封装的动画变量的动画矩形边界。  
  
```  
CAnimationVariable m_leftValue;  
```  
  
##  <a name="m_rightvalue"></a>CAnimationRect::m_rightValue  
 表示右封装的动画变量的动画矩形边界。  
  
```  
CAnimationVariable m_rightValue;  
```  
  
##  <a name="m_szinitial"></a>CAnimationRect::m_szInitial  
 指定动画矩形的初始大小。  
  
```  
CSize m_szInitial;  
```  
  
##  <a name="m_topvalue"></a>CAnimationRect::m_topValue  
 封装的动画变量表示顶部动画矩形的边界。  
  
```  
CAnimationVariable m_topValue;  
```  
  
##  <a name="operator_rect"></a>CAnimationRect::operator RECT  
 将 CAnimationRect 转换为矩形  
  
```  
operator RECT();
```   
  
### <a name="return-value"></a>返回值  
 动画矩形作为矩形的当前值  
  
### <a name="remarks"></a>备注  
 此函数在内部调用 GetValue。 如果出于某种原因 GetValue 失败，则返回的矩形将包含所有矩形坐标的默认值。  
  
##  <a name="operator_eq"></a>CAnimationRect::operator =  
 将 rect 分配给 CAnimationRect。  
  
```  
void operator=(const RECT& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 新的动画矩形的值。  
  
### <a name="remarks"></a>备注  
 建议将动画开始之前执行，原因是此运算符将调用 SetDefaultValue，将已创建的情况下重新创建颜色组件的基础 COM 对象。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。  
  
##  <a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue  
 设置默认值。  
  
```  
void SetDefaultValue(const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 指定左侧、 顶部、 右侧和底部的新默认的值。  
  
### <a name="remarks"></a>备注  
 使用此函数将默认值设置为动画对象。 此方法将默认值分配给矩形边界。 它还会重新创建底层的 COM 对象未创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

