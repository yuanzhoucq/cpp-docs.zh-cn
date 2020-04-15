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
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360583"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty 类

类`CMFCPropertyGridFileProperty`支持打开文件选择对话框的属性列表控件项。

## <a name="syntax"></a>语法

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC属性网格文件属性：CMFC财产网格文件属性](#cmfcpropertygridfileproperty)|构造 `CMFCPropertyGridFileProperty` 对象。|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyGridFileProperty::OnClickButton`|（覆盖[CMFC 属性网格属性：：单击按钮](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).）|

### <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>要求

**标题：** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFC属性网格文件属性：CMFC财产网格文件属性

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
[在]属性名称。

*b打开文件对话*<br/>
[在]TRUE 打开**打开文件**对话框;FALSE 以打开 **"保存文件"** 对话框。

*strFilename*<br/>
[在]初始文件名。

*lpszDefExt*<br/>
[在]一个或多个文件名扩展名的字符串。 默认值为 NULL。

dwFlags**<br/>
[在]对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。

*lpszFilter*<br/>
[在]一个或多个文件筛选器的字符串。 默认值为 NULL。

*lpszDescr*<br/>
[在]属性项描述。 默认值为 NULL。

*dwData*<br/>
[在]与属性项关联的特定于应用程序的数据。 例如，32 位整数或与指向其他数据的指针。 默认值为 0。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

有关可用标志的完整列表，请参阅[OPENFILENAME 结构](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

### <a name="example"></a>示例

以下示例演示如何使用 `CMFCPropertyGridFileProperty` 类的构造函数创建对象。 此示例是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC财产网格Ctrl类](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
