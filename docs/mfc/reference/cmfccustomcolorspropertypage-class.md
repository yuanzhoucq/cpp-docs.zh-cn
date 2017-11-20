---
title: "CMFCCustomColorsPropertyPage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs: C++
helpviewer_keywords: CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 633d8648cf204b726f46e753c67991b81df5b0cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 类
表示可以在颜色对话框中选择自定义颜色的属性页。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|默认构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCCustomColorsPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|设置的属性页的颜色组件。|  
  
### <a name="remarks"></a>备注  
 `CMFCColorDialog`类使用此类来显示自定义颜色属性页。 有关详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCCustomColorsPropertyPage`对象，并将在属性页的颜色组件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>CMFCCustomColorsPropertyPage::Setup  
 设置的属性页的颜色组件。  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `R`|RGB 值红色组件。|  
|[in] `G`|个 RGB 值的绿色部分。|  
|[in] `B`|蓝色分量的 RGB 值。|  
  
### <a name="remarks"></a>备注  
 此方法将更新当前 RGB 和关联的 HLS （色调、 亮度和饱和度） 颜色值的属性页。 [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)方法框架初始化颜色对话框中或用户按下鼠标左键时调用此方法。 有关详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage 类](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
