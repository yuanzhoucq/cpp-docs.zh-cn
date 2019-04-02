---
title: CMFCToolBarComboBoxEdit 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: 55a2cfef69ee215d63a859b0b7fbf3886bbf60b6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771027"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit 类

框架使用`CMFCToolBarComboBoxEdit`类创建的行为类似于一个可编辑的组合框控件的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|构造 `CMFCToolBarComboBoxEdit` 对象。|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|

### <a name="remarks"></a>备注

从派生类`CMFCToolBarComboBoxEdit`类自定义其编辑操作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>要求

**标头：** afxtoolbarcomboboxbutton.h

##  <a name="cmfctoolbarcomboboxedit"></a>  CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit

构造 `CMFCToolBarComboBoxEdit` 对象。

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>参数

*combo*<br/>
[in]对引用[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象，它是包含一个组合框控件的工具栏按钮。

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCToolBarComboBoxEdit`类。 此代码片段属于[IE 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
