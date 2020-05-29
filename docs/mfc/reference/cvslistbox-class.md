---
title: CVSListBox 类
ms.date: 11/19/2018
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
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373191"
---
# <a name="cvslistbox-class"></a>CVSListBox 类

类`CVSListBox`支持可编辑的列表控件。

## <a name="syntax"></a>语法

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CVSListBox：CVSListBox](#cvslistbox)|构造 `CVSListBox` 对象。|
|`CVSListBox::~CVSListBox`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CVSListBox：：添加项目](#additem)|将字符串添加到列表控件。 （重写 `CVSListBoxBase::AddItem`。）|
|[CVSListBox：编辑项目](#edititem)|对列表控件项的文本启动编辑操作。 （重写 `CVSListBoxBase::EditItem`。）|
|[CVSListBox：获取计数](#getcount)|检索可编辑列表控件中的字符串数。 （重写 `CVSListBoxBase::GetCount`。）|
|[CVSListBox：获取项目数据](#getitemdata)|检索与可编辑列表控制项关联的特定于应用程序的 32 位值。 （重写 `CVSListBoxBase::GetItemData`。）|
|[CVSListBox：获取项目文本](#getitemtext)|检索可编辑列表控制项的文本。 （重写 `CVSListBoxBase::GetItemText`。）|
|[CVSListBox：：获取塞尔项目](#getselitem)|在可编辑列表控件中检索当前选定项的零基索引。 （重写 `CVSListBoxBase::GetSelItem`。）|
|`CVSListBox::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 有关详细信息和方法语法，请参阅[CWnd：:P重新翻译消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CVSListBoxBase::PreTranslateMessage`。）|
|[CVSListBox：删除项目](#removeitem)|从可编辑列表控件中删除项目。 （重写 `CVSListBoxBase::RemoveItem`。）|
|[CVSListBox：选择项目](#selectitem)|选择可编辑的列表控制字符串。 （重写 `CVSListBoxBase::SelectItem`。）|
|[CVSListBox：：设置项目数据](#setitemdata)|将特定于应用程序的 32 位值与可编辑的列表控制项关联。 （重写 `CVSListBoxBase::SetItemData`。）|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CVSListBox：获取列表Hwnd](#getlisthwnd)|将句柄返回到当前嵌入的列表视图控件。|

## <a name="remarks"></a>备注

该`CVSListBox`类提供一组编辑按钮，使用户能够在列表控件中创建、修改、删除或重新排列项目。

以下是可编辑列表控件的图片。 第二个列表条目名为"项目 2"，用于编辑。

![CVSListBox 控件](../../mfc/reference/media/cvslistbox.png "CVSListBox 控件")

如果使用资源编辑器添加可编辑列表控件，请注意编辑器的**Toolbox**窗格不提供预定义的可编辑列表控件。 而是添加静态控件，如**组框**控件。 框架使用静态控件作为占位符来指定可编辑列表控件的大小和位置。

要在对话框模板中使用可编辑的列表控件，请在对话框类中声明`CVSListBox`变量。 要支持变量和控件之间的数据交换，请在对话框`DDX_Control``DoDataExchange`的方法中定义一个宏条目。 默认情况下，无需编辑按钮即可创建可编辑的列表控件。 使用继承的 CVSListBoxBase：：设置标准按钮方法启用编辑按钮。

有关详细信息，请参阅示例目录、`New Controls`示例、Page3.cpp 和 Page3.h 文件。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>要求

**标题：** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox：：添加项目

将字符串添加到列表控件。

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*斯特里克斯特*<br/>
[在]对字符串的引用。

*dwData*<br/>
[在]与字符串关联的特定于应用程序的 32 位值。 默认值为 0。

*iIndex*<br/>
[在]将保存字符串的位置的零基索引。 如果*iIndex*参数为 -1，则字符串将添加到列表的末尾。 默认值为 -1。

### <a name="return-value"></a>返回值

字符串在列表控件中位置的零基索引。

### <a name="remarks"></a>备注

使用[CVSListBox：：getItemData](#getitemdata)方法检索*dwData*参数指定的值。 此值可以是特定于应用程序的整数或指向其他数据的指针。

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox：CVSListBox

构造 `CVSListBox` 对象。

```
CVSListBox();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox：编辑项目

对列表控件项的文本启动编辑操作。

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表控件项的零基索引。

### <a name="return-value"></a>返回值

如果编辑操作成功启动，则为 TRUE;如果编辑操作成功启动，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

用户通过双击项目的标签，或在项目具有焦点时按**F2**或**空格键**来启动编辑操作。

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox：获取计数

检索可编辑列表控件中的字符串数。

```
virtual int GetCount() const;
```

### <a name="return-value"></a>返回值

列表控件中的项数。

### <a name="remarks"></a>备注

请注意，计数大于最后一个项的索引值，因为索引是零基的。

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox：获取项目数据

检索与可编辑列表控制项关联的特定于应用程序的 32 位值。

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]可编辑列表控件项的零基索引。

### <a name="return-value"></a>返回值

与指定项关联的 32 位值。

### <a name="remarks"></a>备注

使用[CVSListBox：：设置项目数据](#setitemdata)或[CVSListBox：addItem](#additem)方法将 32 位值与列表控制项相关联。 此值可以是特定于应用程序的整数或指向其他数据的指针。

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox：获取项目文本

检索可编辑列表控制项的文本。

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]可编辑列表控件项的零基索引。

### <a name="return-value"></a>返回值

包含指定项文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

### <a name="remarks"></a>备注

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox：获取列表Hwnd

将句柄返回到当前嵌入的列表视图控件。

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>返回值

嵌入列表视图控件的句柄。

### <a name="remarks"></a>备注

使用此方法检索支持类的嵌入式列表视图控件的`CVSListBox`句柄。

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox：：获取塞尔项目

在可编辑列表控件中检索当前选定项的零基索引。

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>返回值

如果此方法成功，则当前选定项的零基索引;否则，-1。

### <a name="remarks"></a>备注

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox：删除项目

从可编辑列表控件中删除项目。

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]可编辑列表控件项的零基索引。

### <a name="return-value"></a>返回值

如果删除指定的项，则为 TRUE;如果已删除指定项，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox：选择项目

选择可编辑的列表控制字符串。

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
[在]可编辑列表控件项的零基索引。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法选择指定的项，如果需要，则将项滚动到视图中。

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox：：设置项目数据

将特定于应用程序的 32 位值与可编辑的列表控制项关联。

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]可编辑列表控件项的零基索引。

*dwData*<br/>
[在]32 位值。 此值可以是特定于应用程序的整数或指向其他数据的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
