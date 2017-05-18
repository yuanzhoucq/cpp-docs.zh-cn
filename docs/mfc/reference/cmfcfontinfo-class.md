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
- CMFCFontInfo class
- CMFCFontInfo::CMFCFontInfo constructor
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ac1409bcfce389cbc334edd2b864f7505d7443c7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 类
`CMFCFontInfo`类描述的名称和其他属性的一种字体。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|[CMFCFontInfo::GetFullName](#getfullname)|检索的一种字体和其字符的串联的名称设置 （脚本）。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|一个值，指定与字体相关的字符集 （脚本）。|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|一个值，指定的间距和字体系列。|  
|[CMFCFontInfo::m_nType](#m_ntype)|一个值，指定的字体类型。|  
|[CMFCFontInfo::m_strName](#m_strname)|字体; 的名称例如， **Arial**。|  
|[CMFCFontInfo::m_strScript](#m_strscript)|字符集 （脚本） 与字体相关联的名称。|  
  
## <a name="remarks"></a>备注  
 您可以将附加`CMFCFontInfo`对象传递给的项[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)类。 调用[CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法来检索一个指向`CMFCFontInfo`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种成员`CMFCFontInfo`类。 该示例演示如何获取`CMFCFontInfo`对象从`CMFCRibbonFontComboBox`，以及如何访问其本地变量。 此示例摘自[MSOffice 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&6;](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarfontcombobox.h  
  
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
 一个值，指定的间距和字体系列。 有关详细信息，请参阅`lfPitchAndFamily`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
 [in] `nType`  
 一个值，指定的字体类型。 此参数可以为 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的按位组合 (OR)。  
  
 [in] `src`  
 现有`CMFCFontInfo`对象，其成员用于构造此`CMFCFontInfo`对象。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 本文档使用两个术语*字符集*和*脚本*互换。 一个*脚本*，后者也称为是书写系统，是字符和将这些字符写入一个或多个语言版本的规则的集合。 该集合的字符包括的字母表和标点该脚本中使用。 例如，拉丁语脚本适用于英语解说在美国，以及其字母表中包含从 A 到 Z 的字符。`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构指定的字符集。 例如，值`ANSI_CHARSET`指定[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]字符集，其中包括拉丁语脚本的字母表。  
  
##  <a name="getfullname"></a>CMFCFontInfo::GetFullName  
 检索的一种字体和其字符的串联的名称设置 （脚本）。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含字体名称和脚本的字符串。  
  
### <a name="remarks"></a>备注  
 使用此方法以获取字体的完整名称。 例如，如果字体名称是`Arial`以及字体脚本是`Cyrillic`，此方法返回"Arial （西里尔文）"。  
  
##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet  
 一个值，指定与字体相关的字符集 （脚本）。  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nCharSet`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily  
 一个值，指定的间距 （点大小） 和字体的系列 （例如，衬线、 宋体和等宽字体）。  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nPitchAndFamily`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_ntype"></a>CMFCFontInfo::m_nType  
 一个值，指定的字体类型。  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`nType`参数[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)构造函数。  
  
##  <a name="m_strname"></a>CMFCFontInfo::m_strName  
 字体的名称︰ 例如， **Arial**。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox 类](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

