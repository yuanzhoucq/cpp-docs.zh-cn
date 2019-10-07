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
ms.openlocfilehash: 4e6bdef10d5747abd344750c888cf6726c47d99e
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929937"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 类

一个无模式选项卡对话框（ [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)），该对话框允许用户自定义应用程序中的工具栏、菜单、键盘快捷键、用户定义的工具和视觉样式。 通常，用户可从 **“工具”** 菜单中选择 **“自定义”** 来访问此对话框。

"**自定义**" 对话框有六个选项卡：**命令**、**工具栏**、**工具**、**键盘**、**菜单**和**选项**。

## <a name="syntax"></a>语法

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|构造 `CMFCToolBarsCustomizeDialog` 对象。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)|将工具栏按钮插入**命令页上的命令**列表中|
|[CMFCToolBarsCustomizeDialog：： AddMenu](#addmenu)|从资源加载菜单并调用[CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)将该菜单添加到 "**命令**" 页上的命令列表中。|
|[CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)|从资源加载菜单并调用[CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)将该菜单添加到 "**命令**" 页上的命令列表中。|
|[CMFCToolBarsCustomizeDialog：： AddToolBar](#addtoolbar)|从资源加载工具栏。 然后，对于菜单中的每个命令，都将调用[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法，以便在指定类别下的**命令**页上的命令列表中插入按钮。|
|[CMFCToolBarsCustomizeDialog：： Create](#create)|显示 "**自定义**" 对话框。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|留待将来使用。|
|[CMFCToolBarsCustomizeDialog：： EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|使用 "**自定义**" 对话框启用或禁用创建新的工具栏。|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|用 " `CListBox` **所有命令**" 类别中的命令填充提供的对象。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|在 " `CComboBox` **自定义**" 对话框中，用每个命令类别的名称填充提供的对象。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|在 " `CListBox` **自定义**" 对话框中，用每个命令类别的名称填充提供的对象。|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|检索与给定的命令 ID 相关联的名称。|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|检索提供的列表中具有给定文本标签的项的数目。|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|检索影响对话框行为的标志集。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCToolBarsCustomizeDialog：： OnEditToolbarMenuImage](#onedittoolbarmenuimage)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|重写以增加属性表初始化。 （重写[CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。）|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|在销毁窗口后由框架调用。 （重写 `CPropertySheet::PostNcDestroy`。）|
|[CMFCToolBarsCustomizeDialog：： RemoveButton](#removebutton)|从指定的类别或所有类别中删除具有指定命令 ID 的按钮。|
|[CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory)|重命名 "**命令**" 选项卡上类别列表框中的类别。|
|[CMFCToolBarsCustomizeDialog：： ReplaceButton](#replacebutton)|使用新的工具栏按钮对象替换 "**命令**" 选项卡上命令列表中的按钮。|
|[CMFCToolBarsCustomizeDialog：： SetUserCategory](#setusercategory)|将类别添加到将在 "**命令**" 选项卡上显示的类别列表中。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog：： CheckToolsValidity](#checktoolsvalidity)|由框架调用，以确定用户定义的工具列表是否有效。|
|[CMFCToolBarsCustomizeDialog：： OnAfterChangeTool](#onafterchangetool)|当用户定义的工具的属性更改时，由框架调用。|
|[CMFCToolBarsCustomizeDialog：： OnAssignKey](#onassignkey)|确定是否可以为操作分配指定的键盘快捷方式。|
|[CMFCToolBarsCustomizeDialog：： OnBeforeChangeTool](#onbeforechangetool)|确定是否可以更改用户定义的工具。|
|[CMFCToolBarsCustomizeDialog：： OnInitToolsPage](#oninittoolspage)|在请求用户选择 "**工具**" 选项卡时由框架调用。|

## <a name="remarks"></a>备注

若要显示 "**自定义**" 对话框， `CMFCToolBarsCustomizeDialog`请创建对象并调用[CMFCToolBarsCustomizeDialog：： create](#create)方法。

当 "**自定义**" 对话框处于活动状态时，应用程序将以一种特定模式工作，该模式将用户限制为自定义任务。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarsCustomizeDialog` 类中的各种方法。 该示例演示如何在 "**命令**" 页上的命令的列表框中替换工具栏按钮、启用使用 "**自定义**" 对话框创建新工具栏以及显示 "**自定义**" 对话框。 此代码片段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>要求

**标头：** afxToolBarsCustomizeDialog

##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog：： AddButton

将工具栏按钮插入 "**命令**" 页上的命令列表中。

```
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

*uiCategoryId*<br/>
中指定要在其中插入按钮的类别 ID。

*鼠标*<br/>
中指定要插入的按钮。

*iInsertBefore*<br/>
中指定工具栏按钮的从零开始的索引，在此处插入按钮。

*lpszCategory*<br/>
中指定要插入按钮的类别字符串。

### <a name="remarks"></a>备注

方法忽略具有标准命令 id （如 ID_FILE_MRU_FILE1）的按钮、不允许的命令（请参阅[CMFCToolBar：： IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)）和虚按钮。 `AddButton`

此方法使用按钮的运行时类创建一个与`button` （通常是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)）相同的类型的新对象。 然后调用[CMFCToolBarButton：： CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)以复制按钮的数据成员，并将该副本插入指定的类别。

插入 "新建" 按钮时，会收到`OnAddToCustomizePage`通知。

如果`iInsertBefore`为-1，则该按钮将追加到类别列表中; 否则，它将插入具有指定索引的项之前。

### <a name="example"></a>示例

下面的示例演示如何使用`AddButton` `CMFCToolBarsCustomizeDialog`类的方法。 此代码片段是[滑块示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog：： AddMenu

从资源加载菜单并调用[CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)将该菜单添加到 "**命令**" 页上的命令列表中。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>参数

*uiMenuResId*<br/>
中指定要加载的菜单的资源 ID。

### <a name="return-value"></a>返回值

如果已成功添加菜单，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在对的调用`AddMenuCommands`中， *bPopup*为 FALSE。 因此，该方法不会将包含子菜单的菜单项添加到命令列表中。 此方法会将子菜单中的菜单项添加到命令列表中。

##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog：： AddMenuCommands

将项添加到 "**命令**" 页中的命令列表，以表示指定菜单中的所有项。

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
中指向要添加的 CMenu 对象的指针。

*bPopup*<br/>
中指定是否在命令列表中插入弹出菜单项。

*lpszCategory*<br/>
中要插入菜单的类别的名称。

*lpszMenuPath*<br/>
中当命令显示在 "**所有类别**" 列表中时添加到名称中的前缀。

### <a name="remarks"></a>备注

方法遍历 pMenu 的所有菜单项。 `AddMenuCommands` 对于不包含子菜单的每个菜单项，此方法将创建一个[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象，并调用[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法，将菜单项作为工具栏按钮添加到**命令**页。 在此过程中将忽略分隔符。

如果*bPopup*为 TRUE，则对于包含子菜单的每个菜单项，此方法将创建一个[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并通过调用`AddButton`将其插入到命令列表中。 否则，包含子菜单的菜单项不会显示在命令列表中。 在这两种情况`AddMenuCommands`下，当遇到带有子菜单的菜单项时，它会以递归方式自行调用，并将子菜单的指针作为*pMenu*参数传递，并将子菜单的标签追加到*lpszMenuPath*。

##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog：： AddToolBar

从资源加载工具栏。 然后，对于菜单中的每个命令，都将调用[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法，以便在指定类别下的**命令**页上的命令列表中插入按钮。

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>参数

*uiCategoryId*<br/>
中指定要将工具栏添加到的类别的资源 ID。

*uiToolbarResId*<br/>
中指定工具栏的资源 ID，其命令插入到命令列表中。

*lpszCategory*<br/>
中指定要向其添加工具栏的类别的名称。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="example"></a>示例

下面的示例演示如何使用`AddToolBar` `CMFCToolBarsCustomizeDialog`类中的方法。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>备注

用于表示每个命令的控件是一个[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。 添加工具栏后，可以通过调用[CMFCToolBarsCustomizeDialog：： ReplaceButton](#replacebutton)将按钮替换为派生类型的控件。

##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog：： CheckToolsValidity

验证用户工具列表的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>参数

*lstTools*<br/>
中要检查的用户定义工具的列表。

### <a name="return-value"></a>返回值

如果用户定义的工具列表有效，则返回 TRUE;否则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

框架调用此方法来验证表示由[CMFCToolBarsCustomizeDialog：： CheckToolsValidity](#checktoolsvalidity)返回的用户定义工具的对象的有效性。

如果要`CheckToolsValidity`在用户关闭对话框之前验证`CMFCToolBarsCustomizeDialog`用户工具，请重写派生自的类中的方法。 如果用户单击对话框右上角的 "**关闭**" 按钮或对话框右下角标记为 "**关闭**" 按钮时，此方法返回 FALSE，则对话框将显示 "**工具**" 选项卡而不是结束语. 如果此方法在用户单击某个选项卡时返回 FALSE **，则不**会发生导航。 应显示相应的消息框，通知用户导致验证失败的问题。

##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog：： CMFCToolBarsCustomizeDialog

构造 `CMFCToolBarsCustomizeDialog` 对象。

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>参数

*pWndParentFrame*<br/>
中指向父帧的指针。 此参数不得为 NULL。

*bAutoSetFromMenus*<br/>
中一个布尔值，指定是否将所有菜单中的菜单命令添加到 "**命令**" 页上的命令列表中。 如果此参数为 TRUE，则将添加菜单命令。 否则，不会添加菜单命令。

*uiFlags*<br/>
中影响对话框行为的标志的组合。 此参数可以是以下一个或多个值：

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
中一个指针，指向指定其他`CRuntimeClass`自定义页的对象的列表。

### <a name="remarks"></a>备注

*PlistCustomPages*参数是指`CRuntimeClass`对象的列表，这些对象指定了其他自定义页。 构造函数通过使用[CRuntimeClass：： CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法向对话框添加更多页。 有关将更多页面添加到 "**自定义**" 对话框的示例，请参阅 CustomPages 示例。

有关可以在*uiFlags*参数中传递的值的详细信息，请参阅[CMFCToolBarsCustomizeDialog：： GetFlags](#getflags)。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarsCustomizeDialog`类的对象。 此代码片段是[自定义页面示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>CMFCToolBarsCustomizeDialog：： Create

显示 "**自定义**" 对话框。

```
virtual BOOL Create();
```

### <a name="return-value"></a>返回值

如果成功创建自定义属性表，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅在完全初始化类后调用方法。`Create`

##  <a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog：： EnableUserDefinedToolbars

使用 "**自定义**" 对话框启用或禁用创建新的工具栏。

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中若要启用用户定义的工具栏，则为 TRUE;若要禁用工具栏，则为 FALSE。

### <a name="remarks"></a>备注

如果*bEnable*为 TRUE，则**新**的、**重命名**和**删除**按钮将显示在 "**工具栏**" 页上。

默认情况下，如果*bEnable*为 FALSE，则不会显示这些按钮，并且用户无法定义新的工具栏。

##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog：： FillAllCommandsList

用 " `CListBox` **所有命令**" 类别中的命令填充提供的对象。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>参数

*wndListOfCommands*<br/>
弄对要填充的`CListBox`对象的引用。

### <a name="remarks"></a>备注

"**所有命令**" 类别包含所有类别的命令。 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法将与提供的按钮关联的命令添加到 "**所有命令**" 类别。

此方法在用 "**所有命令**" `CListBox`类别中的命令填充所提供的对象之前清除其内容。

`CMFCMousePropertyPage`类使用此方法来填充双击事件列表框。

##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog：： FillCategoriesComboBox

在 " `CComboBox` **自定义**" 对话框中，用每个命令类别的名称填充提供的对象。

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wndCategory*<br/>
弄对要填充的`CComboBox`对象的引用。

*bAddEmpty*<br/>
中一个布尔值，指定是否向没有命令的组合框中添加类别。 如果此参数为 TRUE，则将空类别添加到组合框。 否则，不会添加空的类别。

### <a name="remarks"></a>备注

此方法类似于[CMFCToolBarsCustomizeDialog：： FillCategoriesListBox](#fillcategorieslistbox)方法，但此方法与`CComboBox`对象一起使用。

此方法不会在填充`CComboBox`对象之前清除其内容。 它确保 "**所有命令**" 类别为组合框中的最后一项。

您可以使用[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法添加新的命令类别。 您可以使用[CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory)方法更改现有类别的名称。

`CMFCToolBarsKeyboardPropertyPage` 和`CMFCKeyMapDialog`类使用此方法对键盘映射进行分类。

##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog：： FillCategoriesListBox

在 " `CListBox` **自定义**" 对话框中，用每个命令类别的名称填充提供的对象。

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wndCategory*<br/>
弄对要填充的`CListBox`对象的引用。

*bAddEmpty*<br/>
中一个布尔值，指定是否将没有命令的列表添加到列表框。 如果此参数为 TRUE，则空类别将添加到列表框中。 否则，不会添加空的类别。

### <a name="remarks"></a>备注

此方法类似于[CMFCToolBarsCustomizeDialog：： FillCategoriesComboBox](#fillcategoriescombobox)方法，但此方法与`CListBox`对象一起使用。

此方法不会在填充`CListBox`对象之前清除其内容。 它确保 "**所有命令**" 类别是列表框中的最后一项。

您可以使用[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法添加新的命令类别。 您可以使用[CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory)方法更改现有类别的名称。

`CMFCToolBarsCommandsPropertyPage`类使用此方法来显示与每个命令类别关联的命令的列表。

##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog：： GetCommandName

检索与给定的命令 ID 相关联的名称。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中要检索的命令的 ID。

### <a name="return-value"></a>返回值

与给定的命令 ID 相关联的名称; 如果该命令不存在，则为 NULL。

##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog：： GetCountInCategory

检索提供的列表中具有给定文本标签的项的数目。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>参数

*lpszItemName*<br/>
中要匹配的文本标签。

*lstCommands*<br/>
中对包含`CMFCToolBarButton`对象的列表的引用。

### <a name="return-value"></a>返回值

提供的列表中其文本标签等于*lpszItemName*的项数。

### <a name="remarks"></a>备注

提供的对象列表中的每个元素都必须`CMFCToolBarButton`是类型。 此方法将*lpszItemName*与[CMFCToolBarButton：： m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)数据成员进行比较。

##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog：： GetFlags

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
|AFX_CUSTOMIZE_MENU_SHADOWS|允许用户指定菜单的阴影外观。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允许用户指定是否在工具栏按钮图像下显示文本标签。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允许用户指定菜单动画样式。  |
|AFX_CUSTOMIZE_NOHELP|从 "自定义" 对话框中删除 "帮助" 按钮。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|启用 WS_EX_CONTEXTHELP 视觉样式。  |
|AFX_CUSTOMIZE_NOTOOLS|从 "自定义" 对话框中删除 "**工具**" 页。 如果你的`CUserToolsManager`应用程序使用类，则此标志有效。  |
|AFX_CUSTOMIZE_MENUAMPERS|允许按钮标题包含 "and" 符 **&** （）字符。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|从 "自定义" 对话框中删除 "**大图标**" 选项。  |

有关 WS_EX_CONTEXTHELP 视觉样式的详细信息，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

##  <a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog：： OnAfterChangeTool

在用户工具发生更改后立即响应更改。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[in，out]指向已更改的用户工具对象的指针。

### <a name="remarks"></a>备注

当用户更改用户定义工具的属性时，框架会调用此方法。 默认实现不执行任何操作。 在从派生的`CMFCToolBarsCustomizeDialog`类中重写此方法，以在对用户工具进行更改后执行处理。

##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog：： OnAssignKey

验证用户定义的键盘快捷方式。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>参数

*pAccel*<br/>
[in，out]指向建议的键盘分配的指针，该指针表示为[加速](/windows/win32/api/winuser/ns-winuser-accel)结构。

### <a name="return-value"></a>返回值

如果可以分配密钥，则为 TRUE; 否则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

在派生类中重写此方法，以在用户分配新的键盘快捷方式时执行额外的处理，或在用户定义键盘快捷方式时进行验证。 若要防止分配快捷方式，则返回 FALSE。 还应显示一个消息框，或通知用户键盘快捷方式被拒绝的原因。

##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog：： OnBeforeChangeTool

当用户要应用更改时，在用户工具发生更改时执行自定义处理。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[in，out]指向即将被替换的用户工具对象的指针。

### <a name="remarks"></a>备注

当用户定义工具的属性将要更改时，框架会调用此方法。 默认实现不执行任何操作。 如果要`OnBeforeChangeTool`在对用户工具进行更改`CMFCToolBarsCustomizeDialog`之前执行处理（如释放*pSelTool*使用的资源），请重写派生自的类中的方法。

##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog：： OnEditToolbarMenuImage

启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向父窗口的指针。

*bitmap*<br/>
中对要编辑的位图对象的引用。

*nBitsPerPixel*<br/>
中位图颜色分辨率（以每像素位数为单位）。

### <a name="return-value"></a>返回值

如果正在提交更改，则为 TRUE;否则为 FALSE。 默认实现显示一个对话框，如果用户单击 **"确定"** ，则返回 TRUE; 如果用户单击 "**取消**" 或 "**关闭**" 按钮，则返回 FALSE。

### <a name="remarks"></a>备注

当用户运行图像编辑器时，框架会调用此方法。 默认实现显示 " [CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)" 对话框。 在`OnEditToolbarMenuImage`派生类中重写，以使用自定义图像编辑器。

##  <a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog：： OnInitDialog

重写以增加属性表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

调用[CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法的结果。

### <a name="remarks"></a>备注

此方法通过以下方式扩展基类实现[： CPropertySheet：： OnInitDialog：](../../mfc/reference/cpropertysheet-class.md#oninitdialog)显示 "**关闭**" 按钮，通过确保对话框符合当前屏幕大小，并将 "**帮助**" 按钮移动到左下角来扩展对话框。

##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog：： OnInitToolsPage

从框架处理要初始化的**工具**页的通知。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>备注

默认实现不执行任何操作。 在派生类中重写此方法以处理此通知。

##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog：:P ostNcDestroy

在销毁窗口后由框架调用。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>备注

此方法通过将应用程序还原到`CPropertySheet::PostNcDestroy`以前的模式来扩展基类实现。

[CMFCToolBarsCustomizeDialog：： Create](#create)方法会将应用程序置于特殊模式，以限制用户自定义任务。

##  <a name="removebutton"></a>CMFCToolBarsCustomizeDialog：： RemoveButton

从指定的类别或所有类别中删除具有指定命令 ID 的按钮。

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>参数

*uiCategoryId*<br/>
中指定要从中删除按钮的类别 ID。

*uiCmdId*<br/>
中指定按钮的命令 ID。

*lpszCategory*<br/>
中指定从中删除该按钮的类别的名称。

### <a name="return-value"></a>返回值

已移除按钮的从零开始的索引; 如果在指定的类别中找不到指定的命令 ID，则为-1。 如果*uiCategoryId*为-1，则返回值为0。

### <a name="remarks"></a>备注

若要从所有类别中删除按钮，请调用此方法的第一个重载，并将*uiCategoryId*设置为-1。

##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog：： RenameCategory

重命名 "**命令**" 页上类别列表框中的类别。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>参数

*lpszCategoryOld*<br/>
中要更改的类别名称。

*lpszCategoryNew*<br/>
中新类别名称。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

类别名称必须是唯一的。

##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog：： ReplaceButton

替换 "**命令**" 页上命令列表框中的工具栏按钮。

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中指定要替换的按钮的命令。

*鼠标*<br/>
中对替换旧按钮的工具栏按钮对象的**常量**引用。

### <a name="remarks"></a>备注

当[CMFCToolBarsCustomizeDialog：： AddMenu](#addmenu)、 [CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)或[CMFCToolBarsCustomizeDialog：： AddToolBar](#addtoolbar)将命令添加到 "**命令**" 页时，该命令的格式[为CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象（或包含`AddMenuCommands`添加的子菜单的菜单项的[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象）。 框架还会调用这三个方法自动添加命令。 如果要改为通过派生类型来表示命令，请调用`ReplaceButton`并传入派生类型的按钮。

### <a name="example"></a>示例

下面的示例演示如何使用`ReplaceButton` `CMFCToolBarsCustomizeDialog`类中的方法。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog：： SetUserCategory

指定 "**命令**" 页上的类别列表中的哪个类别是用户类别。 在调用[CMFCToolBarsCustomizeDialog：： Create](#create)之前，必须调用此函数。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>参数

*lpszCategory*<br/>
中类别的名称。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

框架当前不使用用户类别设置。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)
