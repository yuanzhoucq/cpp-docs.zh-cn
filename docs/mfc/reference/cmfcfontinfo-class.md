---
title: CMFCFontInfo 类
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367485"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 类

类`CMFCFontInfo`描述字体的名称和其他属性。

## <a name="syntax"></a>语法

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCFontInfo`|构造 `CMFCFontInfo` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC方信息：获取全名](#getfullname)|检索字体及其字符集（脚本）的串联名称。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC方信息：：m_nCharSet](#m_ncharset)|指定与字体关联的字符集（脚本）的值。|
|[CMFC方信息：m_nPitchAndFamily](#m_npitchandfamily)|指定字体的间距和族的值。|
|[CMFC方信息：m_nType](#m_ntype)|指定字体类型的值。|
|[CMFC方信息：m_strName](#m_strname)|字体的名称;例如 **，Arial**。|
|[CMFC方信息：：m_strScript](#m_strscript)|与字体关联的字符集（脚本）的名称。|

## <a name="remarks"></a>备注

您可以将`CMFCFontInfo`对象附加到[CMFCToolBarFontCombox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)的项。 调用[CMFCToolBarFontCombox：getFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法以检索指向`CMFCFontInfo`对象的指针。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCFontInfo`类的各个成员。 该示例演示如何从`CMFCFontInfo``CMFCRibbonFontComboBox`获取 对象以及如何访问其局部变量。 此示例是[MSOffice 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afxtoolbarfontcombox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFC方信息：CMFC方信息

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

*lpsz名称*<br/>
[在]字体的名称。 有关详细信息，请参阅`lfFaceName`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

*lpszScript*<br/>
[在]字体的脚本（字符集）的名称。

*nCharSet*<br/>
[在]指定字体的字符集（脚本）的值。 有关详细信息，请参阅`lfCharSet`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

*n 皮奇和家庭*<br/>
[在]指定字体的间距和族的值。 有关详细信息，请参阅`lfPitchAndFamily`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

nType**<br/>
[在]指定字体类型的值。 此参数可以是DEVICE_FONTTYPE、RASTER_FONTTYPE和TRUETYPE_FONTTYPE的位组合 （OR）。

*src*<br/>
[在]其成员用于`CMFCFontInfo`构造此`CMFCFontInfo`对象的现有对象。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

本文档可互换使用术语*字符集*和*脚本*。 *脚本*（也称为书写系统）是用一种或多种语言书写这些字符的字符和规则的集合。 字符的集合包括该脚本中使用的字母表和标点符号。 例如，拉丁语脚本用于英语，因为它在美国使用，其字母表包括从A到Z的字符。`lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员指定字符集。 例如，值ANSI_CHARSET指定 ANSI 字符集，其中包括拉丁脚本的字母表。

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFC方信息：获取全名

检索字体及其字符集（脚本）的串联名称。

```
CString GetFullName() const;
```

### <a name="return-value"></a>返回值

包含字体名称和脚本的字符串。

### <a name="remarks"></a>备注

使用此方法获取字体的全名。 例如，如果字体名称为**Arial，** 并且字体脚本为**西里尔，** 则此方法返回"Arial（西里尔）"。

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFC方信息：：m_nCharSet

指定与字体关联的字符集（脚本）的值。

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 CMFCFontInfo 的*nCharSet*参数[：：CMFCFontInfo](#cmfcfontinfo)构造函数。

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFC方信息：m_nPitchAndFamily

指定字体的间距（点大小）和族（例如，衬线、无衬线和单一空间）的值。

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 CMFCFontInfo 的*nPitch 和系列*参数[：：CMFCFontInfo](#cmfcfontinfo)构造函数。

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFC方信息：m_nType

指定字体类型的值。

```
const int m_nType;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 CMFCFontInfo 的*nType*参数[：：CMFCFontInfo](#cmfcfontinfo)构造函数。

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFC方信息：m_strName

字体的名称：例如 **，Arial**。

```
const CString m_strName;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 CMFCFontInfo 的*lpszName*参数[：：CMFCFontInfo](#cmfcfontinfo)构造函数。

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFC方信息：：m_strScript

与字体关联的字符集（脚本）的名称。

```
const CString m_strScript;
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 CMFCFontInfo 的*lpszScript*参数[：：CMFCFontInfo](#cmfcfontinfo)构造函数。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox 类](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
