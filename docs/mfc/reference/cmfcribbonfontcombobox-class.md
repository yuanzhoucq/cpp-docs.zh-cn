---
title: CMFCRibbonFontComboBox 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79facf2498769c0f4385f6dbc84133c3773fe0e7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705678"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 类
实现包含字体列表的组合框。 将组合框置于功能区面板上。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|析构函数。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|构造并初始化一个 `CMFCRibbonFontComboBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|使用具有指定字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|  
|`CMFCRibbonFontComboBox::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|返回指定字符集。|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|返回组合框中显示的字体的间距和系列。|  
|`CMFCRibbonFontComboBox::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|使用具有以前指定的字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|选择组合框中的指定字体。|  
  
## <a name="remarks"></a>备注  
 在创建后`CMFCRibbonFontComboBox`对象，将其添加到功能区面板，通过调用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts  
 使用填充在功能区字体组合框。  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>参数  
*nFontType*<br/>
[in]指定要添加的字体的字体类型。  
  
*nCharSet*<br/>
[in]指定要添加的字体的字符集。  
  
*nPitchAndFamily*<br/>
[in]指定的间距和要添加的字体系列。  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 构造并初始化[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)对象。  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>参数  
*nID*<br/>
[in]当用户从组合框中选择某个项时执行命令的命令 ID。  
  
*nFontType*<br/>
[in]指定要在组合框中显示哪种字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。  
  
*nCharSet*<br/>
[in]筛选器中组合框为属于指定的字符集的字体...  
  
*nPitchAndFamily*<br/>
[in]指定的间距和组合框中显示的字体系列。  
  
*nWidth*<br/>
[in]指定以像素为单位，组合框的宽度。  
  
### <a name="remarks"></a>备注  
 有关可能的详细信息*nFontType*参数值，请参阅[EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) Windows SDK 文档中。  
  
 详细了解可以分配给有效字符集*nCharSet*，并可以分配给的有效值*nPitchAndFamily*，请参阅[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)中Windows SDK 文档。  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*iIndex*  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 填充组合框使用字体功能区上的以前指定的字体类型、 字符集和间距和系列。  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>备注  
 您可以指定字体类型、 字符集以及间距和要包含在功能区字体组合框中的字体系列框中[构造函数](#cmfcribbonfontcombobox)对于此类，或通过调用[CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
 选择组合框中的指定字体。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>参数  
 lpszName *  
 指定要选择的字体的名称。  
  
 *nCharSet*  
 指定所选字体的字符集。  
  
 *bExact*  
 指定选择一种字体; 时，必须匹配的字符组，则返回 TRUE选择一种字体时，可以忽略 FALSE 以指定的字符集。  
  
### <a name="return-value"></a>返回值  
 如果找到并选择; 指定的字体，非零值否则为为零。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 返回指定字符集。  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>返回值  
 字符集 （请参阅 Windows SDK 文档中的 LOGFONT）。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>返回值  
 （请参阅 Windows SDK 文档中的 EnumFontFamProc） 的字体类型。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
 返回组合框中显示的字体的间距和系列。  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>返回值  
 间距和系列 （请参阅 Windows SDK 文档中的 LOGFONT）。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox 类](../../mfc/reference/cmfcribboncombobox-class.md)
