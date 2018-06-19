---
title: CCustomTransition 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
dev_langs:
- C++
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89c3ec260fad8b0e2f8224c639aa745a9101e8b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358036"
---
# <a name="ccustomtransition-class"></a>CCustomTransition 类
实现自定义转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|构造一个自定义转换对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|设置将应用于此转换与关联的动画变量初始值。|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|设置初始的速度，它们将应用于此转换与关联的动画变量。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定是否使用 SetInitialValue 指定初始值。|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定是否使用 SetInitialVelocity 指定的初始速度。|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|存储的初始的值。|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|将存储的初始速度。|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|存储指向自定义插值程序。|  
  
## <a name="remarks"></a>备注  
 CCustomTransitions 类允许开发人员来实现自定义的转换。 它已创建并用作一个标准转换，但其构造函数将作为参数接受指向自定义插值程序。 执行以下步骤以使用自定义的转换： 1。 CCustomInterpolator 派生一个类和至少实现 InterpolateValue 方法。 2. 确保必须超过的动画持续时间中仍在使用自定义插值程序对象的生存期。 3. 实例化 （使用 new 运算符） CCustomTransition 对象并将指针传递到构造函数中的自定义插值程序。 4. 调用 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity，如果这些参数所需的自定义的内插。 5. 将指针传递给自定义转换到 AddTransition 方法的动画对象，其值应使用自定义算法进行动画处理。 6. 当动画对象的值应更改 Windows 动画 API 将在 CCustomInterpolator 调用 InterpolateValue （和其他相关的方法）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition  
 构造一个自定义转换对象。  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>参数  
 `pInterpolator`  
 指向自定义插值程序的指针。  
  
##  <a name="create"></a>  CCustomTransition::Create  
 调用要创建封装的转换 COM 对象的转换库。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>参数  
 `pFactory`  
 指向转换工厂，其负责创建的自定义转换的指针。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 此方法还可以设置初始值和要应用于此转换与关联的动画变量的初始速度。 为此目的，你需要调用 SetInitialValue 和 SetInitialVelocity 之前框架创建 （它发生在调用 CAnimationController::AnimateGroup 时） 的封装的转换 COM 对象。  
  
##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified  
 指定是否使用 SetInitialValue 指定初始值。  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified  
 指定是否使用 SetInitialVelocity 指定的初始速度。  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue  
 存储的初始的值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity  
 将存储的初始速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator  
 存储指向自定义插值程序。  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue  
 设置将应用于此转换与关联的动画变量初始值。  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity  
 设置初始的速度，它们将应用于此转换与关联的动画变量。  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialVelocity`  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
