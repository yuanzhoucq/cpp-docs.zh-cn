---
title: CConstantTransition 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48a8ccb49001b93ded52edc732fc59222775e6f8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954022"
---
# <a name="cconstanttransition-class"></a>CConstantTransition 类
封装常量转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CConstantTransition::CConstantTransition](#cconstanttransition)|构造转换对象并初始化其持续时间。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CConstantTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CConstantTransition::m_duration](#m_duration)|转换的持续时间。|  
  
## <a name="remarks"></a>备注  
 常量在转换期间，动画变量的值保持为初始值期间的转换。 由于所有转换并自动都清除，则建议你到分配它们使用新的运算符。 封装的 IUIAnimationTransition COM 对象被创建通过 CAnimationController::AnimateGroup，直到，然后它为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CConstantTransition`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="cconstanttransition"></a>  CConstantTransition::CConstantTransition  
 构造转换对象并初始化其持续时间。  
  
```  
CConstantTransition (UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>参数  
 *持续时间*  
 转换的持续时间。  
  
##  <a name="create"></a>  CConstantTransition::Create  
 调用要创建封装的转换 COM 对象的转换库。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>参数  
 *pLibrary*  
 指向的指针[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  

### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="m_duration"></a>  CConstantTransition::m_duration  
 转换的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
