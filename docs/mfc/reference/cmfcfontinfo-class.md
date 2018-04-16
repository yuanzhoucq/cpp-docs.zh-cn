---
title: "CMFCFontInfo 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0ea0572667ef45264fd52934cd2d4ee750a6d4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 类
`CMFCFontInfo`类描述的名称和字体的其他特性。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCFontInfo`|构造 `CMFCFontInfo` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCFontInfo::GetFullName](#getfullname)|检索字体和它的字符的串联的名称设置 （脚本）。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|一个值，指定与字体相关联的字符集 （脚本）。|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|一个值，指定的间距和系列的字体。|  
|[CMFCFontInfo::m_nType](#m_ntype)|一个值，指定的字体的类型。|  
|[CMFCFontInfo::m_strName](#m_strname)|字体; 的名称例如， **Arial**。|  
|[CMFCFontInfo::m_strScript](#m_strscript)|字符集 （脚本） 与字体相关联的名称。|  
  
## <a name="remarks"></a>备注  
 你可以将附加`CMFCFontInfo`到的项的对象[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)类。 调用[CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法来检索指向的指针`CMFCFontInfo`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用的不同成员`CMFCFontInfo`类。 该示例演示如何获取`CMFCFontInfo`对象`CMFCRibbonFontComboBox`，以及如何访问其本地变量。 此示例摘自[MSOffice 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头：** afxtoolbarfontcombobox.h  
  
##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo  
 构造 `CMFCFontInfo` 对象。  
  
```  
CMFCFontInfo(
    LPCTSTR lpszName,  
    LPCTSTR lpszScript,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily,  
    int nType);  
  
CMFCFontInfo(const CMFCFontInfo& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 字体的名称。 有关详细信息，请参阅`lfFaceName`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in] `lpszScript`  
 脚本 （字符集） 的字体的名称。  
  
 [in] `nCharSet`  
 一个值，指定的字体的字符集 （脚本）。 有关详细信息，请参阅`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in] `nPitchAndFamily`  
 一个值，指定的间距和系列的字体。 有关详细信息，请参阅`lfPitchAndFamily`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in] `nType`  
 一个值，指定的字体类型。 此参数可以是 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的按位组合 (OR)。  
  
 [in] `src`  
 现有`CMFCFontInfo`其成员用于构造此对象`CMFCFontInfo`对象。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 本文档使用的词汇*字符集*和*脚本*互换。 A*脚本*，即也称为书写系统，是字符和在一个或多个语言中编写这些字符的规则的集合。 字符集合包括字母和标点在该脚本中使用。 例如，拉丁脚本用于英语，因为它在美国，读出和其字母表中包含的字符从 A 到 Z 消息。`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构指定字符集。 例如，值`ANSI_CHARSET`指定[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]字符组，其中包括拉丁语字母表。  
  
##  <a name="getfullname"></a>CMFCFontInfo::GetFullName  
 检索字体和它的字符的串联的名称设置 （脚本）。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个字符串，包含的字体名称和脚本。  
  
### <a name="remarks"></a>备注  
 使用此方法以获取字体的完整名称。 例如，字体名称的情况是`Arial`以及字体脚本是`Cyrillic`，此方法返回"Arial （西里尔文）"。  
  
##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet  
 一个值，指定与字体相关联的字符集 （脚本）。  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nCharSet`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily  
 一个值，指定的间距 （点大小） 和的字体系列 （例如，serif、 宋体，和 monospace）。  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nPitchAndFamily`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_ntype"></a>CMFCFontInfo::m_nType  
 一个值，指定的字体的类型。  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nType`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_strname"></a>CMFCFontInfo::m_strName  
 字体的名称： 例如， **Arial**。  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`lpszName`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_strscript"></a>CMFCFontInfo::m_strScript  
 字符集 （脚本） 与字体相关联的名称。  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`lpszScript`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox 类](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
