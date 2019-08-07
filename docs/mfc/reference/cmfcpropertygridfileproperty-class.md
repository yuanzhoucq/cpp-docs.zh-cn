---
title: CMFCPropertyGridFileProperty 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 4b64d18a67ea499c202b81481684227200846483
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821285"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty 类

`CMFCPropertyGridFileProperty`类支持用于打开文件选择对话框的属性列表控件项。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|构造 `CMFCPropertyGridFileProperty` 对象。|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyGridFileProperty::OnClickButton`|(重写[CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

### <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>要求

**标头:** afxpropertygridctrl

##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty:: CMFCPropertyGridFileProperty

构造 `CMFCPropertyGridFileProperty` 对象。

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*strName*<br/>
中属性名称。

*bOpenFileDialog*<br/>
中若要打开 "**打开文件**" 对话框, 则为 TRUE;若要打开 "**保存文件**" 对话框, 则为 FALSE。

*strFileName*<br/>
中初始文件名。

*lpszDefExt*<br/>
中一个或多个文件扩展名的字符串。 默认值为 NULL。

*dwFlags*<br/>
中对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。

*lpszFilter*<br/>
中一个或多个文件筛选器的字符串。 默认值为 NULL。

*lpszDescr*<br/>
中属性项说明。 默认值为 NULL。

*dwData*<br/>
中与属性项关联的特定于应用程序的数据。 例如，32 位整数或与指向其他数据的指针。 默认值为 0。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

有关可用标志的完整列表, 请参阅[OPENFILENAME 结构](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

### <a name="example"></a>示例

以下示例演示如何使用 `CMFCPropertyGridFileProperty` 类的构造函数创建对象。 此示例是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
