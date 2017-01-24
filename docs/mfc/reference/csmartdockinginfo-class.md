---
title: "CSmartDockingInfo Class | Microsoft Docs"
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
  - "CSmartDockingInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSmartDockingInfo class"
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSmartDockingInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义智能标记停靠外观。  
  
## 语法  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CSmartDockingInfo::CSmartDockingInfo`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSmartDockingInfo::CopyTo](../Topic/CSmartDockingInfo::CopyTo.md)|复制当前智能停靠的信息参数到提供的 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) 对象。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSmartDockingInfo::m\_bUseThemeColorInShading](../Topic/CSmartDockingInfo::m_bUseThemeColorInShading.md)|指定是否使用当前主题颜色框架时显示智能标记停靠。|  
|[CSmartDockingInfo::m\_clrBaseBackground](../Topic/CSmartDockingInfo::m_clrBaseBackground.md)|指定智能标记停靠的基本背景色。|  
|[CSmartDockingInfo::m\_clrToneDest](../Topic/CSmartDockingInfo::m_clrToneDest.md)|指定替换在智能标记停靠位图的 `m_clrToneSrc` 的颜色。|  
|[CSmartDockingInfo::m\_clrToneSrc](../Topic/CSmartDockingInfo::m_clrToneSrc.md)|指定智能标记停靠位图的颜色。|  
|[CSmartDockingInfo::m\_clrTransparent](../Topic/CSmartDockingInfo::m_clrTransparent.md)|但透明时，指定智能标记停靠位图的颜色。|  
|[CSmartDockingInfo::m\_nCentralGroupOffset](../Topic/CSmartDockingInfo::m_nCentralGroupOffset.md)|指定智能标记停靠的中心组的偏移量中心组矩形的边界。|  
|[CSmartDockingInfo::m\_sizeTotal](../Topic/CSmartDockingInfo::m_sizeTotal.md)|在组中指定所有智能标记停靠的总大小。|  
|[CSmartDockingInfo::m\_uiMarkerBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerBmpResID.md)|定义框架为智能标记停靠使用未显示位图的资源ID。|  
|[CSmartDockingInfo::m\_uiMarkerLightBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerLightBmpResID.md)|定义框架为智能标记停靠使用显示位图的资源ID。|  
  
## 备注  
 内部结构处理智能标记停靠。  下图显示了标准智能标记:停靠  
  
 ![标准智能停靠标记](../../mfc/reference/media/nextsdmarkers.png "nextSDmarkers")  
  
 在此图中，图像在左侧显示没有停靠到启用的选项的中央组智能标记停靠。  图像将在中间显示一个右边缘智能标记停靠。  在右侧图像显示具有停靠到启用的选项的中央组智能标记停靠。  中心组智能标记停靠有一个母版位图和五个智能标记停靠位图。  
  
 您可以自定义智能标记停靠的以下参数:  
  
-   颜色。  例如，您可以将任何用户定义的颜色替换标记的蓝色在该图中的。  
  
-   透明度颜色。  
  
-   一种的停靠标记的偏移量在中心组中从边框的边框。  
  
-   委托中心组的主要位图。  
  
-   表示规则和显示的智能标记停靠的位图。  
  
 下图显示自定义智能标记停靠的示例:  
  
 ![自定义智能停靠标记](../../mfc/reference/media/nextsdmarkerscustom.png "nextSDmarkersCustom")  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## 要求  
 **标头:** afxDockingManager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)