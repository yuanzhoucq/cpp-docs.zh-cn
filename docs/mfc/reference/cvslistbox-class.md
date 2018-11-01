---
title: CVSListBox 类
ms.date: 11/04/2016
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: e44fa868fc573efbf89bb00147f670298f633381
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513758"
---
# <a name="cvslistbox-class"></a>CVSListBox 类

`CVSListBox`类支持的可编辑列表控件。

## <a name="syntax"></a>语法

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|构造 `CVSListBox` 对象。|
|`CVSListBox::~CVSListBox`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|将字符串添加到列表控件。 （重写 `CVSListBoxBase::AddItem`。）|
|[CVSListBox::EditItem](#edititem)|启动对文本的列表控件项的编辑操作。 （重写 `CVSListBoxBase::EditItem`。）|
|[CVSListBox::GetCount](#getcount)|检索一个可编辑列表控件中的字符串数。 （重写 `CVSListBoxBase::GetCount`。）|
|[CVSListBox::GetItemData](#getitemdata)|检索与可编辑列表控件项相关联的特定于应用程序的 32 位值。 （重写 `CVSListBoxBase::GetItemData`。）|
|[CVSListBox::GetItemText](#getitemtext)|检索可编辑列表控件项的文本。 （重写 `CVSListBoxBase::GetItemText`。）|
|[CVSListBox::GetSelItem](#getselitem)|检索一个可编辑列表控件中当前选定项的从零开始的索引。 （重写 `CVSListBoxBase::GetSelItem`。）|
|`CVSListBox::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关详细信息和方法语法，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CVSListBoxBase::PreTranslateMessage`。）|
|[CVSListBox::RemoveItem](#removeitem)|从一个可编辑列表控件中移除的项。 （重写 `CVSListBoxBase::RemoveItem`。）|
|[CVSListBox::SelectItem](#selectitem)|选择一个可编辑列表控件字符串。 （重写 `CVSListBoxBase::SelectItem`。）|
|[CVSListBox::SetItemData](#setitemdata)|将特定于应用程序的 32 位值的可编辑列表控件项与相关联。 （重写 `CVSListBoxBase::SetItemData`。）|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|返回当前的嵌入的列表视图控件的图柄。|

## <a name="remarks"></a>备注

`CVSListBox`类提供了一组使用户能够创建、 修改、 删除或重新排列列表控件中的项的编辑按钮。

以下是可编辑列表控件的图片。 标题为"Item2"的第二个列表项选择进行编辑。

![CVSListBox 控件](../../mfc/reference/media/cvslistbox.png "cvslistbox")

如果使用资源编辑器将添加一个可编辑列表控件，请注意**工具箱**编辑器窗格中不提供预定义的可编辑列表控件。 相反，如添加静态控件**分组框**控件。 框架使用静态控件作为占位符，以指定的大小和可编辑列表控件的位置。

若要在对话框模板中使用的可编辑列表控件，声明`CVSListBox`对话框类中用户定义变量。 若要支持变量和控件之间的数据交换，定义`DDX_Control`中的宏条目`DoDataExchange`对话框的方法。 默认情况下，没有编辑按钮的情况下创建可编辑列表控件。 使用继承的 CVSListBoxBase::SetStandardButtons 方法启用的编辑按钮。

有关详细信息，请参阅示例目录中，`New Controls`示例 Page3.cpp 和 Page3.h 文件。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>要求

**标头：** afxvslistbox.h

##  <a name="additem"></a>  CVSListBox::AddItem

将字符串添加到列表控件。

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*strIext*<br/>
[in]对字符串的引用。

*dwData*<br/>
[in]一个与字符串相关联的特定于应用程序的 32 位值。 默认值为 0。

*iIndex*<br/>
[in]将保存的字符串的位置的从零开始的索引。 如果*iIndex*参数为-1，则字符串添加到列表的末尾。 默认值为 -1。

### <a name="return-value"></a>返回值

列表控件中字符串的位置的从零开始索引。

### <a name="remarks"></a>备注

使用[CVSListBox::GetItemData](#getitemdata)方法来检索由指定的值*dwData*参数。 此值可以是特定于应用程序的整数或其他数据的指针。

##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox

构造 `CVSListBox` 对象。

```
CVSListBox();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="edititem"></a>  CVSListBox::EditItem

启动对文本的列表控件项的编辑操作。

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]列表控件项的从零开始的索引。

### <a name="return-value"></a>返回值

如果编辑操作启动成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

用户开始编辑操作，通过双击某一项，标签或通过按**F2**或**空格键**键项具有焦点时。

##  <a name="getcount"></a>  CVSListBox::GetCount

检索一个可编辑列表控件中的字符串数。

```
virtual int GetCount() const;
```

### <a name="return-value"></a>返回值

列表控件中的项数。

### <a name="remarks"></a>备注

请注意因为索引从零开始的计数是一个大于最后一项的索引值。

##  <a name="getitemdata"></a>  CVSListBox::GetItemData

检索与可编辑列表控件项相关联的特定于应用程序的 32 位值。

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]可编辑列表控件项的从零开始的索引。

### <a name="return-value"></a>返回值

与指定项关联的 32 位值。

### <a name="remarks"></a>备注

使用[CVSListBox::SetItemData](#setitemdata)或[CVSListBox::AddItem](#additem)方法来将 32 位值与列表控件项相关联。 此值可以是特定于应用程序的整数或其他数据的指针。

##  <a name="getitemtext"></a>  CVSListBox::GetItemText

检索可编辑列表控件项的文本。

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]可编辑列表控件项的从零开始的索引。

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含指定项的文本。

### <a name="remarks"></a>备注

##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd

返回当前的嵌入的列表视图控件的图柄。

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>返回值

嵌入的列表视图控件的句柄。

### <a name="remarks"></a>备注

使用此方法来检索支持嵌入的列表视图控件的句柄`CVSListBox`类。

##  <a name="getselitem"></a>  CVSListBox::GetSelItem

检索一个可编辑列表控件中当前选定项的从零开始的索引。

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>返回值

如果此方法成功，当前选定项的从零开始的索引否则为-1。

### <a name="remarks"></a>备注

##  <a name="removeitem"></a>  CVSListBox::RemoveItem

从一个可编辑列表控件中移除的项。

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]可编辑列表控件项的从零开始的索引。

### <a name="return-value"></a>返回值

如果指定的项被删除; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="selectitem"></a>  CVSListBox::SelectItem

选择一个可编辑列表控件字符串。

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
[in]可编辑列表控件项的从零开始的索引。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法选择指定的项，如果它是必需的则将该项滚动到视图。

##  <a name="setitemdata"></a>  CVSListBox::SetItemData

将特定于应用程序的 32 位值的可编辑列表控件项与相关联。

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]可编辑列表控件项的从零开始的索引。

*dwData*<br/>
[in]一个 32 位值。 此值可以是特定于应用程序的整数或其他数据的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
