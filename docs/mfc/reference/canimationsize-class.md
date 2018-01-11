---
title: "CAnimationSize 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs: C++
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2acbdad3ec5b08ef5d83b3a6cfdb2eadd3c0e17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="canimationsize-class"></a>CAnimationSize 类
实现可对大小对象的维度进行动画处理的大小对象功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|已重载。 将构造一个动画大小对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|为宽度和高度添加转换。|  
|[CAnimationSize::GetCX](#getcx)|提供对表示宽度 CAnimationVariable 访问。|  
|[CAnimationSize::GetCY](#getcy)|提供对表示高度 CAnimationVariable 访问。|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|返回默认值为宽度和高度。|  
|[CAnimationSize::GetValue](#getvalue)|返回当前值。|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|设置默认值。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|将封装的动画变量放入列表。 (重写[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|将 CAnimationSize 转换为 CSize。|  
|[CAnimationSize::operator =](#operator_eq)|将 szSrc 分配给 CAnimationSize。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|封装的动画变量表示动画大小的宽度。|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|封装的动画变量表示动画大小的高度。|  
  
## <a name="remarks"></a>备注  
 CAnimationSize 类封装两个 CAnimationVariable 对象，并可以表示在应用程序大小。 例如，你可以使用此类进行动画处理的任何两个大小在屏幕上的维对象 (如矩形，控制等)。 若要在应用程序中使用此类，只需实例化此类的对象、 将其添加到动画控制器使用 CAnimationController::AddAnimationObject 然后调用为每个转换的 AddTransition 要应用于宽度和/或高度。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>惠?  
 **标头：** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationSize::AddTransition  
 为宽度和高度添加转换。  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>参数  
 `pCXTransition`  
 指向宽度的转换的指针。  
  
 `pCYTransition`  
 指向高度的转换的指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可将指定的转换添加到内部列表的转换应用于动画变量的宽度和高度。 添加转换时，它们都不会立即应用和存储在内部列表。 转换将应用 （添加到情节提要特定值） 时调用 CAnimationController::AnimateGroup。 如果你不需要将转换应用于维度之一，则可以传递 NULL。  
  
##  <a name="canimationsize"></a>CAnimationSize::CAnimationSize  
 将构造一个动画大小对象。  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 `szDefault`  
 指定默认大小。  
  
 `nGroupID`  
 指定组 id。  
  
 `nObjectID`  
 指定对象 id。  
  
 `dwUserData`  
 指定用户定义的数据。  
  
### <a name="remarks"></a>备注  
 对象构造使用的宽度、 高度，默认值的对象 ID 和组 ID，将设置为 0。 它们可以在运行时使用 SetDefaultValue 和 SetID 更高版本更改。  
  
##  <a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList  
 将封装的动画变量放入列表。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>参数  
 `lst`  
 当函数返回时，它包含指向表示的宽度和高度的两个 CAnimationVariable 对象的指针。  
  
##  <a name="getcx"></a>CAnimationSize::GetCX  
 提供对表示宽度 CAnimationVariable 访问。  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示宽度的引用。  
  
### <a name="remarks"></a>备注  
 你可以调用此方法以获取对基础 CAnimationVariable 表示宽度的直接访问权限。  
  
##  <a name="getcy"></a>CAnimationSize::GetCY  
 提供对表示高度 CAnimationVariable 访问。  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>返回值  
 对封装 CAnimationVariable 表示高度的引用。  
  
### <a name="remarks"></a>备注  
 你可以调用此方法以获取对基础 CAnimationVariable 表示高度的直接访问权限。  
  
##  <a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue  
 返回默认值为宽度和高度。  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>返回值  
 一个包含默认值 CSize 对象。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索之前已由构造函数或 SetDefaultValue 设置的默认值。  
  
##  <a name="getvalue"></a>CAnimationSize::GetValue  
 返回当前值。  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>参数  
 `szValue`  
 输出。 此方法返回时包含的当前值。  
  
### <a name="return-value"></a>返回值  
 已成功检索的当前值; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索动画大小的当前值。 如果此方法失败或尚未初始化基础 COM 对象的宽度和大小，szValue 包含在构造函数中或通过 SetDefaultValue 之前已设置的默认值。  
  
##  <a name="m_cxvalue"></a>CAnimationSize::m_cxValue  
 封装的动画变量表示动画大小的宽度。  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>CAnimationSize::m_cyValue  
 封装的动画变量表示动画大小的高度。  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>CAnimationSize::operator CSize  
 将 CAnimationSize 转换为 CSize。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>返回值  
 作为 CSize 动画大小的当前值。  
  
### <a name="remarks"></a>备注  
 此函数内部调用 GetValue。 如果出于某种原因 GetValue 失败，返回的大小将包含默认值为宽度和高度。  
  
##  <a name="operator_eq"></a>CAnimationSize::operator =  
 将 szSrc 分配给 CAnimationSize。  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>参数  
 `szSrc`  
 指 CSize 或大小。  
  
### <a name="remarks"></a>备注  
 将 szSrc 分配给 CAnimationSize。 建议你先执行该操作早动画开始日期，原因是此运算符将调用 SetDefaultValue，重新基础 COM 对象创建的宽度和高度，如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 为此动画对象，你需要重新启用这些事件。  
  
##  <a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue  
 设置默认值。  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>参数  
 `szDefault`  
 指定新的默认大小。  
  
### <a name="remarks"></a>备注  
 使用此函数将默认值设置为动画对象。 此方法将默认值分配给动画大小的宽度和高度。 它还重新创建基础 COM 对象，如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 为此动画对象，你需要重新启用这些事件。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
