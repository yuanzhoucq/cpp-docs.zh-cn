---
title: CMFCToolBarsCustomizeDialog 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
ms.openlocfilehash: 29e2c3d0238ac5a084ea916d95ad953f8c4aedce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753398"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 类

一个无模式选项卡对话框 （ [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)）， 使用户能够自定义应用程序中的工具栏、菜单、键盘快捷键、用户定义的工具和视觉样式。 通常，用户可从 **“工具”** 菜单中选择 **“自定义”** 来访问此对话框。

**"自定义"** 对话框有六个选项卡：**命令**、**工具栏**、**工具**、**键盘**、**菜单**和**选项**。

## <a name="syntax"></a>语法

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC工具栏自定义对话框：：CMFC工具栏自定义对话框](#cmfctoolbarscustomizedialog)|构造 `CMFCToolBarsCustomizeDialog` 对象。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC工具栏自定义对话：：添加按钮](#addbutton)|将工具栏按钮插入**命令页上的命令**列表中|
|[CMFC工具栏自定义对话：：添加菜单](#addmenu)|从资源加载菜单并调用[CMFCToolBars自定义对话框：添加Menu命令](#addmenucommands)以将该菜单添加到**命令**页面上的命令列表中。|
|[CMFC工具栏自定义对话：：添加菜单命令](#addmenucommands)|从资源加载菜单并调用[CMFCToolBars自定义对话框：添加Menu命令](#addmenucommands)以将该菜单添加到**命令**页面上的命令列表中。|
|[CMFC工具栏自定义对话框：：添加工具栏](#addtoolbar)|从资源加载工具栏。 然后，对于菜单中的每个命令，调用[CMFCToolBars自定义对话框：：AddButton](#addbutton)方法，在指定类别下**的命令**页上的命令列表中插入一个按钮。|
|[CMFC工具栏自定义对话：：创建](#create)|显示 **"自定义"** 对话框。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供将来使用。|
|[CMFC工具栏自定义对话框：：启用用户定义的工具栏](#enableuserdefinedtoolbars)|使用 **"自定义"** 对话框启用或禁用创建新工具栏。|
|[CMFC工具栏自定义对话框：：填充所有命令列表](#fillallcommandslist)|使用`CListBox`**"所有命令"** 类别中的命令填充提供的对象。|
|[CMFC工具栏自定义对话：：填充类别组合框](#fillcategoriescombobox)|使用`CComboBox`**"自定义"** 对话框中每个命令类别的名称填充提供的对象。|
|[CMFC工具栏自定义对话框：：填充类别列表框](#fillcategorieslistbox)|使用`CListBox`**"自定义"** 对话框中每个命令类别的名称填充提供的对象。|
|[CMFC工具栏自定义对话框：：获取命令名称](#getcommandname)|检索与给定命令 ID 关联的名称。|
|[CMFC工具栏自定义对话：：获取计数类别](#getcountincategory)|检索提供列表中具有给定文本标签的项数。|
|[CMFC工具栏自定义对话：：获取 Flags](#getflags)|检索影响对话框行为的标志集。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC工具栏自定义对话框：：编辑工具栏菜单图像](#onedittoolbarmenuimage)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|
|[CMFC工具栏自定义对话：：oninitDialog](#oninitdialog)|用于增强属性表初始化的重写。 （覆盖[C 属性表：oninitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).）|
|[CMFC工具栏自定义对话：:Postnc销毁](#postncdestroy)|窗口被破坏后由框架调用。 （重写 `CPropertySheet::PostNcDestroy`。）|
|[CMFC工具栏自定义对话：：删除按钮](#removebutton)|从指定类别或所有类别中删除具有指定命令 ID 的按钮。|
|[CMFC工具栏自定义对话框：：重命名类别](#renamecategory)|在 **"命令"** 选项卡上的类别列表框中重命名类别。|
|[CMFC工具栏自定义对话：：替换按钮](#replacebutton)|将 **"命令"** 选项卡上命令列表中的按钮替换为新的工具栏按钮对象。|
|[CMFC工具栏自定义对话框：：设置用户类别](#setusercategory)|将类别添加到将显示在 **"命令"** 选项卡上的类别列表中。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC工具栏自定义对话：：检查工具有效性](#checktoolsvalidity)|由框架调用以确定用户定义的工具列表是否有效。|
|[CMFC工具栏自定义对话框：：在更改工具后打开](#onafterchangetool)|当用户定义的工具的属性发生更改时，由框架调用。|
|[CMFC工具栏自定义对话：：在分配键上](#onassignkey)|确定是否可以将指定的键盘快捷方式分配给操作。|
|[CMFC工具栏自定义对话：：在更改工具之前打开](#onbeforechangetool)|确定是否可以更改用户定义的工具。|
|[CMFC工具栏自定义对话：：oninitToolspage](#oninittoolspage)|当用户选择"**工具**"选项卡时，框架调用。|

## <a name="remarks"></a>备注

要显示 **"自定义"** 对话框，请创建`CMFCToolBarsCustomizeDialog`一个对象并调用[CMFCToolBars 自定义对话框：：创建](#create)方法。

当 **"自定义"** 对话框处于活动状态时，应用程序以特殊模式工作，该模式将用户限制为自定义任务。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarsCustomizeDialog` 类中的各种方法。 该示例演示如何在 **"命令"** 页上的命令列表框中替换工具栏按钮，使用 **"自定义"** 对话框启用创建新工具栏，以及显示 **"自定义"** 对话框。 此代码段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>要求

**标题：** afxToolBars自定义对话.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFC工具栏自定义对话：：添加按钮

将工具栏按钮插入到 **"命令"** 页上的命令列表中。

```cpp
void AddButton(
    UINT uiCategoryId,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);
```

### <a name="parameters"></a>参数

*ui 分类 Id*<br/>
[在]指定要插入按钮的类别 ID。

*button*<br/>
[在]指定要插入的按钮。

*iInsert 之前*<br/>
[在]指定工具栏按钮的零索引，在插入按钮之前。

*lpsz类别*<br/>
[在]指定要插入按钮的类别字符串。

### <a name="remarks"></a>备注

该方法`AddButton`忽略具有标准命令 ID（如ID_FILE_MRU_FILE1）、不允许的命令（请参阅[CMFCToolBar：：IsCommand 允许](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)）和虚拟按钮的按钮。

此方法通过使用按钮的运行时类创建与`button`（通常[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)） 类型相同的新对象。 然后调用[CMFCToolBarButton：：从复制](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)以复制按钮的数据成员，并将副本插入到指定的类别中。

插入新按钮时，它将收到`OnAddToCustomizePage`通知。

如果`iInsertBefore`为 -1，则该按钮将追加到类别列表中;如果为 -1，则该按钮将追加到类别列表中。否则，它将插入具有指定索引的项之前。

### <a name="example"></a>示例

下面的示例演示如何使用`AddButton``CMFCToolBarsCustomizeDialog`类的方法。 此代码段是[滑块示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFC工具栏自定义对话：：添加菜单

从资源加载菜单并调用[CMFCToolBars自定义对话框：添加Menu命令](#addmenucommands)以将该菜单添加到**命令**页面上的命令列表中。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>参数

*uiMenuResId*<br/>
[在]指定要加载的菜单的资源 ID。

### <a name="return-value"></a>返回值

如果已成功添加菜单，则为 TRUE;如果菜单已成功添加，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

在调用`AddMenuCommands`中 *，bPopup*是 FALSE。 因此，该方法不会将包含子菜单的菜单项添加到命令列表中。 此方法会将子菜单中的菜单项添加到命令列表中。

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFC工具栏自定义对话：：添加菜单命令

将项添加到 **"命令"** 页中的命令列表中，以表示指定菜单中的所有项。

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
[在]指向要添加的 CMenu 对象的指针。

*bPopup*<br/>
[在]指定是否将弹出菜单项插入到命令列表中。

*lpsz类别*<br/>
[在]要插入菜单的类别的名称。

*lpszMenuPath*<br/>
[在]当命令显示在 **"所有类别"** 列表中时添加到名称的前缀。

### <a name="remarks"></a>备注

该方法`AddMenuCommands`循环访问*pMenu*的所有菜单项。 对于不包含子菜单的每个菜单项，此方法将创建一个[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象，并调用[CMFCToolBar 自定义对话框：：AddButton](#addbutton)方法，将菜单项作为工具栏按钮添加到**命令**页上的命令列表中。 在此过程中将忽略分隔符。

如果*bPopup*为 TRUE，则对于包含子菜单的每个菜单项，此方法创建一个[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并通过调用`AddButton`将其插入到命令列表中。 否则，包含子菜单的菜单项不会显示在命令列表中。 在这两种情况下，当`AddMenuCommands`遇到菜单项与子菜单时，它调用自身递归，将指向子菜单的指针作为*pMenu*参数传递，并将子菜单的标签追加到*lpszMenuPath*。

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFC工具栏自定义对话框：：添加工具栏

从资源加载工具栏。 然后，对于菜单中的每个命令，调用[CMFCToolBars自定义对话框：：AddButton](#addbutton)方法，在指定类别下**的命令**页上的命令列表中插入一个按钮。

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>参数

*ui 分类 Id*<br/>
[在]指定要向其添加工具栏的类别的资源 ID。

*uiToolbarResId*<br/>
[在]指定其命令插入到命令列表中的工具栏的资源 ID。

*lpsz类别*<br/>
[在]指定要向其添加工具栏的类别的名称。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="example"></a>示例

下面的示例演示如何在`AddToolBar``CMFCToolBarsCustomizeDialog`类中使用 方法。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>备注

用于表示每个命令的控件是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。 添加工具栏后，可以通过调用[CMFCToolBars自定义对话框：：：替换按钮](#replacebutton)，将按钮替换为派生类型的控件。

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFC工具栏自定义对话：：检查工具有效性

验证用户工具列表的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>参数

*lstTools*<br/>
[在]要检查的用户定义工具的列表。

### <a name="return-value"></a>返回值

如果用户定义的工具列表有效，则返回 TRUE;否则 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

框架调用此方法来验证表示[CMFCToolBars 自定义对话框](#checktoolsvalidity)返回的用户定义工具的对象的有效性：：检查工具有效性 。

如果要在`CheckToolsValidity`用户关闭对话框之前验证用户`CMFCToolBarsCustomizeDialog`工具，请覆盖派生的类中的方法。 如果用户单击对话框右上角的 **"关闭**"按钮或对话框右下角标记为"**关闭**"的按钮时，此方法将返回 FALSE，则该对话框将显示 **"工具**"选项卡，而不是关闭。 如果用户单击选项卡以从 **"工具"** 选项卡导航时返回 FALSE，则不会发生导航。 应显示一个适当的消息框，以通知用户导致验证失败的问题。

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFC工具栏自定义对话框：：CMFC工具栏自定义对话框

构造 `CMFCToolBarsCustomizeDialog` 对象。

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>参数

*pwnd 父框架*<br/>
[在]指向父帧的指针。 此参数不能为 NULL。

*b自动从菜单中设置*<br/>
[在]布尔值，用于指定是否将所有菜单中的菜单命令添加到 **"命令"** 页上的命令列表中。 如果此参数为 TRUE，则添加菜单命令。 否则，将不会添加菜单命令。

*uiFlags*<br/>
[在]影响对话框行为的标志的组合。 此参数可以是以下一个或多个值：

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plist 自定义页面*<br/>
[在]指向指定其他自定义页的对象`CRuntimeClass`列表的指针。

### <a name="remarks"></a>备注

*plistCustomPages*参数是指指定其他自定义页面`CRuntimeClass`的对象列表。 构造函数使用[CRuntimeClass：：createObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法向对话框添加更多页面。 有关向 **"自定义"** 对话框添加更多页面的示例，请参阅自定义页面示例。

有关可以在*uiFlags*参数中传递的值的详细信息，请参阅[CMFCToolBars自定义对话框：：getFlags](#getflags)。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarsCustomizeDialog`类的对象。 此代码段是[自定义页示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFC工具栏自定义对话：：创建

显示 **"自定义"** 对话框。

```
virtual BOOL Create();
```

### <a name="return-value"></a>返回值

如果自定义属性表已成功创建，则为 TRUE;如果自定义属性表已成功创建，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

仅在完全`Create`初始化类后调用 方法。

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFC工具栏自定义对话框：：启用用户定义的工具栏

使用 **"自定义"** 对话框启用或禁用创建新工具栏。

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用用户定义的工具栏;FALSE 以禁用工具栏。

### <a name="remarks"></a>备注

如果*启用*为 TRUE，则**New**"新建 **"重命名**和**删除**按钮将显示在**工具栏**页上。

默认情况下，或者如果*bEnable*是 FALSE，则不显示这些按钮，并且用户无法定义新的工具栏。

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFC工具栏自定义对话框：：填充所有命令列表

使用`CListBox`**"所有命令"** 类别中的命令填充提供的对象。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>参数

*wndList命令*<br/>
[出]对要填充的对象`CListBox`的引用。

### <a name="remarks"></a>备注

"**所有命令"** 类别包含所有类别的命令。 [CMFCToolBars自定义对话框：AddButton](#addbutton)方法将与您提供的按钮关联的命令添加到 **"所有命令"** 类别。

此方法清除提供`CListBox`的对象的内容，然后再使用 **"所有命令"** 类别中的命令填充它。

类`CMFCMousePropertyPage`使用此方法填充双击事件列表框。

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFC工具栏自定义对话：：填充类别组合框

使用`CComboBox`**"自定义"** 对话框中每个命令类别的名称填充提供的对象。

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wnd分类*<br/>
[出]对要填充的对象`CComboBox`的引用。

*bAddEmpty*<br/>
[在]指定是否向没有命令的组合框添加类别的布尔值。 如果此参数为 TRUE，则空类别将添加到组合框中。 否则，不会添加空类别。

### <a name="remarks"></a>备注

此方法类似于[CMFCToolBars 自定义对话框：：填充类别列表框](#fillcategorieslistbox)方法，但此方法适用于`CComboBox`对象。

此方法在填充`CComboBox`对象之前不会清除对象的内容。 它保证 **"所有命令"** 类别是组合框中的最后一项。

您可以使用[CMFCToolBars 自定义对话框：：addButton](#addbutton)方法添加新的命令类别。 您可以使用[CMFCToolBars自定义对话框：：重命名类别](#renamecategory)方法更改现有类别的名称。

`CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`类使用此方法对键盘映射进行分类。

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFC工具栏自定义对话框：：填充类别列表框

使用`CListBox`**"自定义"** 对话框中每个命令类别的名称填充提供的对象。

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wnd分类*<br/>
[出]对要填充的对象`CListBox`的引用。

*bAddEmpty*<br/>
[在]指定是否将类别添加到没有命令的列表框中的布尔值。 如果此参数为 TRUE，则空类别将添加到列表框中。 否则，不会添加空类别。

### <a name="remarks"></a>备注

此方法类似于[CMFCToolBars 自定义对话框：：填充类别ComboBox](#fillcategoriescombobox)方法，但此方法适用于`CListBox`对象。

此方法在填充`CListBox`对象之前不会清除对象的内容。 它保证 **"所有命令"** 类别是列表框中的最后一项。

您可以使用[CMFCToolBars 自定义对话框：：addButton](#addbutton)方法添加新的命令类别。 您可以使用[CMFCToolBars自定义对话框：：重命名类别](#renamecategory)方法更改现有类别的名称。

类`CMFCToolBarsCommandsPropertyPage`使用此方法显示与每个命令类别关联的命令列表。

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFC工具栏自定义对话框：：获取命令名称

检索与给定命令 ID 关联的名称。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]要检索的命令的 ID。

### <a name="return-value"></a>返回值

与给定命令 ID 关联的名称，如果命令不存在，则为 NULL。

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFC工具栏自定义对话：：获取计数类别

检索提供列表中具有给定文本标签的项数。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>参数

*lpszItem名称*<br/>
[在]要匹配的文本标签。

*lstCommands*<br/>
[在]对包含对象的列表的`CMFCToolBarButton`引用。

### <a name="return-value"></a>返回值

提供列表中的文本标签等于*lpszItemName*的项数。

### <a name="remarks"></a>备注

提供的对象列表中的每个元素必须为 类型`CMFCToolBarButton`。 此方法将*lpszItemName*与[CMFCToolBarButton：：：m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)数据成员进行比较。

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFC工具栏自定义对话：：获取 Flags

检索影响对话框行为的标志集。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>返回值

影响对话框行为的标志集。

### <a name="remarks"></a>备注

此方法检索传递给构造函数的*uiFlags*参数的值。 返回值可以是以下一个或多个值：

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|允许用户指定菜单的卷影外观。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允许用户指定文本标签是否显示在工具栏按钮图像下方。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允许用户指定菜单动画样式。  |
|AFX_CUSTOMIZE_NOHELP|从自定义对话框中删除帮助按钮。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|启用WS_EX_CONTEXTHELP视觉样式。  |
|AFX_CUSTOMIZE_NOTOOLS|从自定义对话框中删除 **"工具"** 页。 如果应用程序使用类，`CUserToolsManager`则此标志有效。  |
|AFX_CUSTOMIZE_MENUAMPERS|允许按钮标题包含安培和 （ **&**） 字符。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|从自定义对话框中删除 **"大图标**"选项。  |

有关WS_EX_CONTEXTHELP视觉样式的详细信息，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFC工具栏自定义对话框：：在更改工具后打开

在用户工具发生后立即响应更改。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[进出]指向已更改的用户工具对象的指针。

### <a name="remarks"></a>备注

当用户更改用户定义工具的属性时，框架将调用此方法。 默认实现不执行任何操作。 在派生的`CMFCToolBarsCustomizeDialog`类中重写此方法，以便对用户工具进行更改后执行处理。

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFC工具栏自定义对话：：在分配键上

在用户定义键盘快捷方式时对其进行验证。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>参数

*pAccel*<br/>
[进出]指向建议的键盘 assigment 的指针，该指针表示为[ACCEL](/windows/win32/api/winuser/ns-winuser-accel)结构。

### <a name="return-value"></a>返回值

如果可以分配密钥，则为 TRUE;如果无法分配密钥，则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

在派生类中重写此方法，以在用户分配新的键盘快捷键时执行额外处理，或在用户定义键盘快捷方式时验证它们。 要防止分配快捷方式，返回 FALSE。 您还应显示消息框或以其他方式通知用户键盘快捷方式被拒绝的原因。

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFC工具栏自定义对话：：在更改工具之前打开

当用户要应用更改时对用户工具进行更改时，执行自定义处理。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[进出]指向即将替换的用户工具对象的指针。

### <a name="remarks"></a>备注

当用户定义工具的属性即将更改时，框架将调用此方法。 默认实现不执行任何操作。 如果要在发生`OnBeforeChangeTool`对用户工具进行更改之前执行`CMFCToolBarsCustomizeDialog`处理，例如释放*pSelTool*使用的资源，请覆盖派生的类中的方法。

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFC工具栏自定义对话框：：编辑工具栏菜单图像

启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向父窗口的指针。

*位图*<br/>
[在]对要编辑的位图对象的引用。

*nBitsPerPixel*<br/>
[在]位图颜色分辨率，以每像素位为单位。

### <a name="return-value"></a>返回值

如果正在实施更改，则为 TRUE;否则 FALSE。 默认实现显示一个对话框，如果用户单击 **"确定"** 或"如果用户单击"**取消"** 或"**关闭**"按钮，则返回 TRUE。

### <a name="remarks"></a>备注

当用户运行图像编辑器时，框架调用此方法。 默认实现显示[CMFCImage 编辑器对话类](../../mfc/reference/cmfcimageeditordialog-class.md)对话框。 在`OnEditToolbarMenuImage`派生类中重写以使用自定义图像编辑器。

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFC工具栏自定义对话：：oninitDialog

用于增强属性表初始化的重写。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

调用[CPropertySheet 的结果：onitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。

### <a name="remarks"></a>备注

此方法通过显示 **"关闭"** 按钮、确保对话框适合当前屏幕大小以及将 **"帮助"** 按钮移动到对话框的左下角来扩展基类实现[CPropertySheet：onInitDialog。](../../mfc/reference/cpropertysheet-class.md#oninitdialog)

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFC工具栏自定义对话：：oninitToolspage

处理框架中有关"**工具"** 页即将初始化的通知。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写派生类中的此方法以处理此通知。

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFC工具栏自定义对话：:Postnc销毁

窗口被破坏后由框架调用。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>备注

此方法通过将应用程序还原到以前的模式来`CPropertySheet::PostNcDestroy`扩展基类实现。

[CMFCToolBars自定义对话框：创建](#create)方法将应用程序置于将用户限制为自定义任务的特殊模式。

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFC工具栏自定义对话：：删除按钮

从指定类别或所有类别中删除具有指定命令 ID 的按钮。

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>参数

*ui 分类 Id*<br/>
[在]指定要从中删除按钮的类别 ID。

*乌伊CmDId*<br/>
[在]指定按钮的命令 ID。

*lpsz类别*<br/>
[在]指定要从中删除按钮的类别的名称。

### <a name="return-value"></a>返回值

删除按钮的零基索引，如果在指定类别中找不到指定的命令 ID，则为 -1。 如果*uiCategoryId*为 -1，则返回值为 0。

### <a name="remarks"></a>备注

要从所有类别中删除按钮，请调用此方法的第一个重载，并将*uiCategoryId*设置为 -1。

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFC工具栏自定义对话框：：重命名类别

在 **"命令"** 页上的类别列表框中重命名类别。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>参数

*lpsz分类Old*<br/>
[在]要更改的类别名称。

*lpsz 分类新*<br/>
[在]新的类别名称。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

类别名称必须是唯一的。

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFC工具栏自定义对话：：替换按钮

在 **"命令"** 页上的命令列表框中替换工具栏按钮。

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]指定要替换的按钮的命令。

*button*<br/>
[在]对替换旧按钮的工具栏按钮对象的**const**引用。

### <a name="remarks"></a>备注

当[CMFCToolBars 自定义对话框：：添加](#addmenu)Menu，CMFCToolBars[自定义对话框：](#addmenucommands)或[CMFCToolBars自定义对话框：addToolBar](#addtoolbar)向**命令**页添加命令时，该命令以[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象（或包含 添加`AddMenuCommands`的子菜单的菜单项的[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象）的形式出现。 框架还调用这三种方法自动添加命令。 如果希望命令由派生类型来表示，请调用`ReplaceButton`并传递派生类型的按钮。

### <a name="example"></a>示例

下面的示例演示如何在`ReplaceButton``CMFCToolBarsCustomizeDialog`类中使用 方法。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFC工具栏自定义对话框：：设置用户类别

指定 **"命令"** 页上的类别列表中的哪个类别是用户类别。 在调用[CMFCToolBars 自定义对话框：：：：创建](#create)之前，必须调用此功能。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>参数

*lpsz类别*<br/>
[在]类别的名称。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

框架当前不使用用户类别设置。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[C属性表类](../../mfc/reference/cpropertysheet-class.md)
