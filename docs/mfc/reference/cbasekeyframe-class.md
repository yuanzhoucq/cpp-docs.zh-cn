---
title: "CBaseKeyFrame 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseKeyFrame"
  - "afxanimationcontroller/CBaseKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseKeyFrame 类"
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBaseKeyFrame 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现关键帧的基本功能。  
  
## 语法  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBaseKeyFrame::CBaseKeyFrame](../Topic/CBaseKeyFrame::CBaseKeyFrame.md)|构造关键帧对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md)|将关键帧添加到情节提要。|  
|[CBaseKeyFrame::GetAnimationKeyframe](../Topic/CBaseKeyFrame::GetAnimationKeyframe.md)|返回基础关键帧值。|  
|[CBaseKeyFrame::IsAdded](../Topic/CBaseKeyFrame::IsAdded.md)|指示是否已将关键帧添加到情节提要。|  
|[CBaseKeyFrame::IsKeyframeAtOffset](../Topic/CBaseKeyFrame::IsKeyframeAtOffset.md)|指定是否应在偏移位置或转换之后将该关键帧添加到情节提要。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CBaseKeyFrame::m\_bAdded](../Topic/CBaseKeyFrame::m_bAdded.md)|指定是否已将此关键帧添加到情节提要。|  
|[CBaseKeyFrame::m\_bIsKeyframeAtOffset](../Topic/CBaseKeyFrame::m_bIsKeyframeAtOffset.md)|指定是否应将此关键帧添加到另一个现有关键帧偏移位置的或某个转换结尾的情节提要。|  
|[CBaseKeyFrame::m\_keyframe](../Topic/CBaseKeyFrame::m_keyframe.md)|表示 Windows 动画 API 关键帧。  当关键帧未进行初始化时，会被设置为预定义的值 UI\_ANIMATION\_KEYFRAME\_STORYBOARD\_START。|  
  
## 备注  
 封装 UI\_ANIMATION\_KEYFRAME 变量。  作为任何关键帧实现的基类。  关键帧表示情节提要中时间的某一时刻，并可用于指定转换的开始时间和结束时间。  有两种类型的关键帧 \- 添加到情节提要的指定偏移位置（以时间表示）的关键帧，或在指定的转换之后添加的关键帧。  因为某些转换的持续时间在动画开始之前无法知道，所以某些关键帧的实际值只能在运行时确定。  因为关键帧可能依赖于转换，而过渡又反过来依赖于关键帧，所以在生成关键帧链时要防止无限递归出现非常重要。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)