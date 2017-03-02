---
title: "CLinearTransitionFromSpeed 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransitionFromSpeed class
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
caps.latest.revision: 18
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: b96ed05e0fbed5fdb6d384f49ca634b4bc7d9269
ms.lasthandoff: 02/24/2017

---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed 类
封装线性速度转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|构造一个线性速度转换对象并初始化其速度和最终值。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|末尾的过渡动画变量的值。|  
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|变量的速度的绝对值。|  
  
## <a name="remarks"></a>备注  
 一个线性速度转换，动画变量的值发生更改以指定速率。 过渡的持续时间由初始值和指定的最终值之间的差异确定。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-nameclineartransitionfromspeeda--clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed::CLinearTransitionFromSpeed  
 构造一个线性速度转换对象并初始化其速度和最终值。  
  
```  
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>参数  
 `dblSpeed`  
 变量的速度的绝对值。  
  
 `dblFinalValue`  
 末尾的过渡动画变量的值。  
  
##  <a name="a-namecreatea--clineartransitionfromspeedcreate"></a><a name="create"></a>CLinearTransitionFromSpeed::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>参数  
`pLibrary`  
 一个指向[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="a-namemdblfinalvaluea--clineartransitionfromspeedmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed::m_dblFinalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdblspeeda--clineartransitionfromspeedmdblspeed"></a><a name="m_dblspeed"></a>CLinearTransitionFromSpeed::m_dblSpeed  
 变量的速度的绝对值。  
  
```  
DOUBLE m_dblSpeed;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

