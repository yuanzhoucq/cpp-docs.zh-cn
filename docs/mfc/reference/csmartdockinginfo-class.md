---
title: CSmartDockingInfo 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
dev_langs:
- C++
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3328eacb9789b892a271208193e82546eb73f7e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373662"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo 类
定义智能停靠标记的外观。  
  
## <a name="syntax"></a>语法  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CSmartDockingInfo::CSmartDockingInfo`|默认构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSmartDockingInfo::CopyTo](#copyto)|将当前智能停靠信息参数复制到提供[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)对象。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|指定是否使用当前的主题颜色时框架显示智能停靠标记。|  
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|指定智能停靠标记的基的背景的色。|  
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|指定用于替换的颜色`m_clrToneSrc`智能停靠标记位图中。|  
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|指定的智能停靠标记位图的颜色。|  
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|指定的智能停靠标记位图的颜色时它们都是透明。|  
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|指定从中央组矩形的边界的智能停靠标记的中央组的偏移量。|  
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|指定组中的所有智能停靠标记的总大小。|  
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|定义的框架用于未突出显示的智能停靠标记的位图的资源 Id。|  
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|定义的框架用于突出显示的智能停靠标记的位图的资源 Id。|  
  
## <a name="remarks"></a>备注  
 Framework 句柄内部智能停靠标记。 下图显示标准智能停靠标记：  
  
 ![标准智能停靠标记](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")  
  
 在此图中，在左侧图显示没有停靠在选项卡启用一个中央组智能停靠标记。 在中间的图像显示右边缘智能停靠标记。 右侧图像显示中央组智能停靠标记不必停靠在启用的选项卡。 中央组智能停靠标记有主位图和五个智能停靠标记位图。  
  
 你可以自定义智能停靠标记的以下参数：  
  
-   颜色。 例如，你可以将图中标记的蓝色颜色替换任何用户定义的颜色。  
  
-   透明度颜色。  
  
-   从边框的边框的中央组中的智能停靠标记的偏移量。  
  
-   用于表示中央组的主位图。  
  
-   表示正则并突出显示的智能停靠标记的位图。  
  
 下图显示已自定义智能停靠标记的一个示例：  
  
 ![自定义智能停靠标记](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxDockingManager.h  
  
##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo  
 将当前智能停靠参数复制到提供[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)对象。  
  
```  
void CopyTo(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>参数  
 [out] `params`  
 类型的对象`CSmartDockingInfo`填充当前智能停靠参数。  
  
##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading  
 指定是否使用当前的主题颜色时框架显示智能停靠标记。  
  
```  
BOOL m_bUseThemeColorInShading;  
```  
  
### <a name="remarks"></a>备注  
 如果`TRUE`，使用当前的主题颜色绘制标记; 否则为浅蓝色绘制标记。  
  
 默认值为 `FALSE`。  
  
##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground  
 指定智能停靠标记的基的背景的色。  
  
```  
COLORREF m_clrBaseBackground;  
```  
  
##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest  
 指定用于将替换的颜色`m_clrToneSrc`智能停靠标记位图中。  
  
```  
COLORREF m_clrToneDest;  
```  
  
### <a name="remarks"></a>备注  
 设置此值以编程方式更改标记位图的颜色。 例如，如果你想要更改的框架提供的标准标记颜色，则将此值设置为所需的颜色。 默认情况下， [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)设置为 RGB （61、 123、 241） （色调蓝色颜色）。  
  
 若要更改自定义标记的颜色，则必须同时指定`m_clrToneDest`和`m_clrToneSrc`。  
  
##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc  
 指定的智能停靠标记位图的颜色。  
  
```  
COLORREF m_clrToneSrc;  
```  
  
### <a name="remarks"></a>备注  
 仅当你想要将自定义位图的颜色替换为另一种颜色，请设置此值。 不需要设置此值，如果您更改一种标准 （框架提供） 的颜色标记。  
  
 使用`(COLORREF)-1`将智能停靠组的成员保留为空。  
  
##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent  
 指定的智能停靠标记位图的颜色时它们都是透明。  
  
```  
COLORREF m_clrTransparent;  
```  
  
### <a name="remarks"></a>备注  
 停靠的组中显示自定义标记和自定义位图时，必须设置此值。  
  
##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset  
 指定的中心小组矩形的边界和智能停靠标记的中央组之间的偏移量。  
  
```  
int m_nCentralGroupOffset;  
```  
  
### <a name="remarks"></a>备注  
 如果你想要更改自定义标记和智能停靠标记的中央组的边界之间的默认偏移量，请指定此值。 默认偏移量为 5 个像素。  
  
##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal  
 指定包含中央组中的所有智能停靠标记的边框的总大小。  
  
```  
CSize m_sizeTotal;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_sizeTotal`中央组标记的边框的大小。 需要指定此值，如果你将自定义位图标记。  
  
##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID  
 定义的用于非突出显示自定义智能停靠标记的位图的资源 Id。  
  
```  
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>备注  
 使用的表示智能停靠标记的位图的资源 Id 填充此数组。 `AFX_SD_MARKERS_NUM` 当前定义为 5。 如下所示填充数组：  
  
 `params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;`  
  
 `params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;`  
  
 `params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;`  
  
 `params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;`  
  
 `params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;`  
  
##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID  
 定义的用于突出显示的自定义智能停靠标记的位图的资源 Id。  
  
```  
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>备注  
 使用的表示突出显示的智能停靠标记的位图的资源 Id 填充此数组。 `AFX_SD_MARKERS_NUM` 当前定义为 5。 如下所示填充数组：  
  
 `params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;`  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)
