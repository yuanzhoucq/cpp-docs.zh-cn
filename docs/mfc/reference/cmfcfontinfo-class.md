---
title: CMFCFontInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2f4a6962ee70882ba85a15ea213f7fe6ffe11f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538226"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 类
`CMFCFontInfo`类描述的名称和字体的其他属性。  
  
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
|[CMFCFontInfo::GetFullName](#getfullname)|检索串联的字体和它的字符的名称集 （脚本）。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|一个值，指定与字体相关的字符集 （脚本）。|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|一个值，指定的间距和系列的字体。|  
|[CMFCFontInfo::m_nType](#m_ntype)|一个值，指定的字体的类型。|  
|[CMFCFontInfo::m_strName](#m_strname)|字体; 的名称例如， **Arial**。|  
|[CMFCFontInfo::m_strScript](#m_strscript)|字符集 （脚本） 与字体相关的名称。|  
  
## <a name="remarks"></a>备注  
 可以将附加`CMFCFontInfo`对象的某个项[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)类。 调用[CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法来检索一个指向`CMFCFontInfo`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种成员`CMFCFontInfo`类。 该示例演示如何获取`CMFCFontInfo`对象从`CMFCRibbonFontComboBox`，以及如何访问其本地变量。 此示例摘自[MSOffice 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** afxtoolbarfontcombobox.h  
  
##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo  
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
 [in]*lpszName*  
 字体的名称。 有关详细信息，请参阅`lfFaceName`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in]*lpszScript*  
 脚本 （字符集） 的字体的名称。  
  
 [in]*nCharSet*  
 一个值，指定的字体的字符集 （脚本）。 有关详细信息，请参阅`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in]*nPitchAndFamily*  
 一个值，指定的间距和系列的字体。 有关详细信息，请参阅`lfPitchAndFamily`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in]*n 类型*  
 一个值，指定的字体类型。 此参数可以是 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的按位组合 (OR)。  
  
 [in]*src*  
 将现有`CMFCFontInfo`对象，其成员用于构造此`CMFCFontInfo`对象。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 本文档使用术语*字符集*并*脚本*互换。 一个*脚本*，这也称为是书写系统，是一系列字符和一个或多个语言中编写这些字符的规则。 字符的集合包括的字母表和标点在该脚本中使用。 例如，拉丁语脚本使用英语解说在美国，以及其字母表中包含从 A 到 Z 的字符。`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构指定字符集。 例如，值 ANSI_CHARSET 指定 ANSI 字符集，其中包括拉丁语脚本的字母表。  
  
##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName  
 检索串联的字体和它的字符的名称集 （脚本）。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含字体名称和脚本的字符串。  
  
### <a name="remarks"></a>备注  
 使用此方法获取完整的字体的名称。 例如，如果字体名称是**Arial** ，该字体脚本便**西里尔文**，此方法返回"Arial （西里尔文）"。  
  
##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet  
 一个值，指定与字体相关的字符集 （脚本）。  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅*nCharSet*的参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily  
 一个值，指定的间距 （磅） 和的字体系列 （例如，衬线、 sans serif 和等宽字体）。  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅*nPitchAndFamily*的参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType  
 一个值，指定的字体的类型。  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅*n 类型*的参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_strname"></a>  CMFCFontInfo::m_strName  
 字体的名称： 例如， **Arial**。  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅*lpszName*的参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript  
 字符集 （脚本） 与字体相关的名称。  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅*lpszScript*的参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox 类](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
