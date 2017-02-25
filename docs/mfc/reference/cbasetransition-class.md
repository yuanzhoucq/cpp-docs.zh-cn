---
title: "CBaseTransition 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseTransition"
  - "afxanimationcontroller/CBaseTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTransition 类"
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CBaseTransition 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示基本转换。  
  
## 语法  
  
```  
class CBaseTransition : public CObject;  
```  
  
## 成员  
  
### 公共枚举  
  
|名称|说明|  
|--------|--------|  
|[CBaseTransition::TRANSITION\_TYPE Enumeration](../Topic/CBaseTransition::TRANSITION_TYPE%20Enumeration.md)|定义 Windows 动画 API 的 MFC 实现当前支持的过渡类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBaseTransition::CBaseTransition](../Topic/CBaseTransition::CBaseTransition.md)|构造基本转换对象。|  
|[CBaseTransition::~CBaseTransition](../Topic/CBaseTransition::~CBaseTransition.md)|该析构函数。  当过渡对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBaseTransition::AddToStoryboard](../Topic/CBaseTransition::AddToStoryboard.md)|将转换添加到情节提要。|  
|[CBaseTransition::AddToStoryboardAtKeyframes](../Topic/CBaseTransition::AddToStoryboardAtKeyframes.md)|将转换添加到情节提要。|  
|[CBaseTransition::Clear](../Topic/CBaseTransition::Clear.md)|释放封装的 IUIAnimationTransition COM 对象。|  
|[CBaseTransition::Create](../Topic/CBaseTransition::Create.md)|创建 COM 转换。|  
|[CBaseTransition::GetEndKeyframe](../Topic/CBaseTransition::GetEndKeyframe.md)|返回开始关键帧。|  
|[CBaseTransition::GetRelatedVariable](../Topic/CBaseTransition::GetRelatedVariable.md)|返回指向相关变量的指针。|  
|[CBaseTransition::GetStartKeyframe](../Topic/CBaseTransition::GetStartKeyframe.md)|返回开始关键帧。|  
|[CBaseTransition::GetTransition](../Topic/CBaseTransition::GetTransition.md)|已重载。  返回指向基础 COM 对象的指针。|  
|[CBaseTransition::GetType](../Topic/CBaseTransition::GetType.md)|返回转换类型。|  
|[CBaseTransition::IsAdded](../Topic/CBaseTransition::IsAdded.md)|指示是否已将转换添加到情节提要。|  
|[CBaseTransition::SetKeyframes](../Topic/CBaseTransition::SetKeyframes.md)|设置转换关键帧。|  
|[CBaseTransition::SetRelatedVariable](../Topic/CBaseTransition::SetRelatedVariable.md)|建立动画变量和转换之间的关系。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CBaseTransition::m\_bAdded](../Topic/CBaseTransition::m_bAdded.md)|指定是否已将转换添加到情节提要。|  
|[CBaseTransition::m\_pEndKeyframe](../Topic/CBaseTransition::m_pEndKeyframe.md)|存储指向指定该过渡结尾的关键帧的指针。|  
|[CBaseTransition::m\_pRelatedVariable](../Topic/CBaseTransition::m_pRelatedVariable.md)|指向使用存储在 m\_transition 中的转换进行动画处理的动画变量的指针。|  
|[CBaseTransition::m\_pStartKeyframe](../Topic/CBaseTransition::m_pStartKeyframe.md)|存储指向指定该转换开始的关键帧的指针。|  
|[CBaseTransition::m\_transition](../Topic/CBaseTransition::m_transition.md)|存储指向 IUIAnimationTransition 的指针。  如果尚未创建 COM 转换对象，则为 NULL。|  
|[CBaseTransition::m\_type](../Topic/CBaseTransition::m_type.md)|存储转换类型。|  
  
## 备注  
 此类封装 IUIAnimationTransition 接口，并作为基类用于所有转换。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)