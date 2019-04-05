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
ms.openlocfilehash: e1dd6fff9fa4f03dbf93510da26c78c73e86c6ab
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780959"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 类

无模式选项卡对话框 ( [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md))，使用户能够自定义工具栏、 菜单、 键盘快捷方式、 用户定义的工具和应用程序中的视觉样式。 通常，用户可从 **“工具”** 菜单中选择 **“自定义”** 来访问此对话框。

**自定义**对话框有六个选项卡：**命令**，**工具栏**，**工具**，**键盘**，**菜单**，并**选项**。

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
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|插入工具栏按钮列表中的命令上**命令**页|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上命令列表添加该菜单**命令**页。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上命令列表添加该菜单**命令**页。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|从资源加载工具栏。 然后，对于每个命令中的菜单中调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法上插入的命令的列表中的按钮**命令**指定类别下的页。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|显示**自定义**对话框。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|留待将来使用。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|启用或禁用通过使用创建新工具栏**自定义**对话框。|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|填充所提供`CListBox`对象中的命令**的所有命令**类别。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|填充所提供`CComboBox`对象中每个命令类别的名称与**自定义**对话框。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|填充所提供`CListBox`对象中每个命令类别的名称与**自定义**对话框。|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|检索与给定的命令 ID 相关联的名称|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|检索具有给定的文本标签提供的列表中的项的数目。|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|检索影响对话框的行为的标志的集。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|重写以增加属性表初始化。 (重写[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|在窗口已销毁之后由框架调用。 （重写 `CPropertySheet::PostNcDestroy`。）|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|从指定的类别，或从所有类别中删除具有指定的命令 ID 的按钮。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|将类别的列表框中的类别上重命名**命令**选项卡。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|在替换的命令的列表中的按钮**命令**使用新的工具栏按钮对象的选项卡。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|将类别添加到将显示在类别列表**命令**选项卡。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|由框架调用以确定是否为有效的用户定义的工具列表。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|用户定义工具的属性更改时由框架调用。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|确定指定的键盘快捷方式是否可以分配给某项操作。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|确定是否可以更改用户定义的工具。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|由框架调用，当用户选择**工具**请求选项卡。|

## <a name="remarks"></a>备注

若要显示**自定义**对话框框中，创建`CMFCToolBarsCustomizeDialog`对象，并调用[CMFCToolBarsCustomizeDialog::Create](#create)方法。

虽然**自定义**对话框处于活动状态，应用程序的工作限制用户访问的自定义任务以特殊模式。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarsCustomizeDialog` 类中的各种方法。 该示例演示如何将命令的列表框中的工具栏按钮上**命令**页上，启用使用创建新工具栏**自定义**对话框中，并显示**自定义**对话框。 此代码片段属于[IE 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>要求

**标头：** afxToolBarsCustomizeDialog.h

##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton

插入工具栏按钮列表中的命令上**命令**页。

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
[in]指定要将按钮插入到其中的类别 ID。

*按钮*<br/>
[in]指定要插入的按钮。

*iInsertBefore*<br/>
[in]指定在其前插入该按钮的工具栏按钮的从零开始索引。

*lpszCategory*<br/>
[in]指定要插入该按钮的类别字符串。

### <a name="remarks"></a>备注

`AddButton`方法将忽略具有标准命令 Id （例如 ID_FILE_MRU_FILE1) 的按钮时，不允许的命令 (请参阅[CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虚拟按钮。

此方法创建新的对象的类型相同`button`(通常[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)) 使用的按钮的运行时类。 然后，它调用[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)要复制的数据成员的按钮，并将该副本插入到指定的类别。

当插入新按钮时，它接收`OnAddToCustomizePage`通知。

如果`iInsertBefore`为-1，按钮追加到的类别列表; 否则为具有指定索引的项之前插入。

### <a name="example"></a>示例

下面的示例演示如何使用`AddButton`方法的`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[滑块示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上命令列表添加该菜单**命令**页。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>参数

*uiMenuResId*<br/>
[in]指定要加载一个菜单资源 ID。

### <a name="return-value"></a>返回值

如果成功，则添加一个菜单，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

在调用`AddMenuCommands`， *bPopup*为 FALSE。 因此，该方法不会添加包含命令列表的子菜单的菜单项。 此方法 does 命令列表，在子菜单中添加菜单项。

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

将项添加到列表中的命令**命令**页上，代表指定的菜单中的所有项。

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>参数

*pMenu*<br/>
[in]指向要添加的 CMenu 对象的指针。

*bPopup*<br/>
[in]指定是否要插入到列表的弹出菜单项的命令。

*lpszCategory*<br/>
[in]要插入菜单的类别的名称。

*lpszMenuPath*<br/>
[in]该命令中显示时添加到名称的前缀**所有类别**列表。

### <a name="remarks"></a>备注

`AddMenuCommands`方法的所有菜单项会循环*pMenu*。 为每个不包含子菜单的菜单项，此方法创建[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象并调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将作为工具栏添加菜单项按钮上的命令的列表**命令**页。 在此过程中，分隔符将被忽略。

如果*bPopup*为 TRUE，对于每个菜单项包含子菜单，此方法创建[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并将其插入到的命令的列表，通过调用`AddButton`。 否则包含子菜单的菜单项不会显示在命令的列表中。 在任一情况下，当`AddMenuCommands`遇到的菜单项在子菜单它本身以递归方式调用，将指针传递到作为子菜单*pMenu*参数并追加到的子菜单的标签*lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

从资源加载工具栏。 然后，对于每个命令中的菜单中调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法上插入的命令的列表中的按钮**命令**指定类别下的页。

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
[in]指定要添加到工具栏类别的资源 ID。

*uiToolbarResId*<br/>
[in]指定的工具栏的命令插入到命令列表的资源 ID。

*lpszCategory*<br/>
[in]指定要向其中添加工具栏的类别的名称。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="example"></a>示例

下面的示例演示如何使用`AddToolBar`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>备注

用于表示每个命令的控件是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。 添加工具栏之后，您可以将按钮替换为派生类型的控件通过调用[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)。

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

验证的用户工具列表的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>参数

*lstTools*<br/>
[in]用户定义的工具来检查的列表。

### <a name="return-value"></a>返回值

返回用户定义的工具的列表是否有效，则为 TRUE否则为 FALSE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

框架调用此方法来验证这些对象表示用户定义的工具，通过返回有效性[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)。

重写`CheckToolsValidity`方法在类中的派生自`CMFCToolBarsCustomizeDialog`如果想要验证的用户工具之前用户关闭对话框。 如果此方法返回 FALSE，当用户单击任一**关闭**右上角的对话框的或标记为按钮的按钮**关闭**右下角的对话框中，对话框显示**工具**而不是关闭的选项卡。 如果此方法返回 FALSE，当用户单击选项卡以导航离开**工具**选项卡上，在导航窗格不会发生。 应显示相应的消息框以通知用户导致验证失败的问题。

##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

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
[in]指向父框架的指针。 此参数不能为 NULL。

*bAutoSetFromMenus*<br/>
[in]一个布尔值，指定是否将菜单命令从所有菜单添加到命令列表，在**命令**页。 如果此参数为 TRUE，将添加的菜单命令。 否则，不会添加的菜单命令。

*uiFlags*<br/>
[in]影响对话框的行为的标志的组合。 此参数可以是一个或多个以下值：

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in]指向一系列的`CRuntimeClass`指定其他自定义页的对象。

### <a name="remarks"></a>备注

*PlistCustomPages*参数引用的列表`CRuntimeClass`指定其他自定义页的对象。 构造函数通过使用向对话框添加更多的页面[CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法。 请参阅 CustomPages 示例有关的示例，将添加到更多的页**自定义**对话框。

有关可以传入的值的详细信息*uiFlags*参数，请参阅[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)。

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[自定义页面示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

显示**自定义**对话框。

```
virtual BOOL Create();
```

### <a name="return-value"></a>返回值

如果成功，则创建自定义属性表，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用`Create`才完全初始化类的方法。

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

启用或禁用通过使用创建新工具栏**自定义**对话框。

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]若要启用用户定义的工具栏;，则返回 TRUE如果为 FALSE 禁用工具栏。

### <a name="remarks"></a>备注

如果*bEnable*为 TRUE，**新建**，**重命名**并**删除**中显示的按钮**工具栏**页。

默认情况下，或者如果*bEnable*为 FALSE，这些按钮不会显示，并且用户不能定义新工具栏。

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

填充所提供`CListBox`对象中的命令**的所有命令**类别。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>参数

*wndListOfCommands*<br/>
[out]对引用`CListBox`要填充对象。

### <a name="remarks"></a>备注

**的所有命令**类别包含的所有类别的命令。 [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将添加到提供的按钮与关联的命令**的所有命令**为您的类别。

此方法会清除所提供的内容`CListBox`之前使用中的命令对其进行填充的对象**的所有命令**类别。

`CMFCMousePropertyPage`类使用此方法来填充双击事件列表框。

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

填充所提供`CComboBox`对象中每个命令类别的名称与**自定义**对话框。

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wndCategory*<br/>
[out]对引用`CComboBox`要填充对象。

*bAddEmpty*<br/>
[in]一个布尔值，该值指定是否要将类别添加到不具有命令的组合框。 如果此参数为 TRUE，那么空类别添加到组合框。 否则，不会添加空的类别。

### <a name="remarks"></a>备注

此方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)方法，但此方法适用于`CComboBox`对象。

此方法不会清除的内容`CComboBox`之前对其进行填充的对象。 它可保证**的所有命令**类别是组合框中的最后一个项目。

您可以通过添加新的命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 可以通过更改现有类别的名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。

`CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`类使用此方法进行分类的键盘映射。

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

填充所提供`CListBox`对象中每个命令类别的名称与**自定义**对话框。

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>参数

*wndCategory*<br/>
[out]对引用`CListBox`要填充对象。

*bAddEmpty*<br/>
[in]一个布尔值，该值指定是否要将类别添加到不具有命令的列表框。 如果此参数为 TRUE，那么空类别添加到列表框。 否则，不会添加空的类别。

### <a name="remarks"></a>备注

此方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)方法，但此方法适用于`CListBox`对象。

此方法不会清除的内容`CListBox`之前对其进行填充的对象。 它可保证**的所有命令**类别是列表框中的最后一项。

您可以通过添加新的命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 可以通过更改现有类别的名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。

`CMFCToolBarsCommandsPropertyPage`类使用此方法来显示与每个命令类别相关联的命令列表。

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

检索与给定的命令 ID 相关联的名称

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
[in]要检索的命令 ID。

### <a name="return-value"></a>返回值

如果该命令不存在与给定的命令 ID 或 NULL 关联的名称。

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

检索具有给定的文本标签提供的列表中的项的数目。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>参数

*lpszItemName*<br/>
[in]要匹配的文本标签。

*lstCommands*<br/>
[in]对一个列表，其中包含的引用`CMFCToolBarButton`对象。

### <a name="return-value"></a>返回值

在所提供的项目数列表的文本标签 equals *lpszItemName*。

### <a name="remarks"></a>备注

提供的对象列表中每个元素必须属于类型`CMFCToolBarButton`。 此方法比较*lpszItemName*与[CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)数据成员。

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

检索影响对话框的行为的标志的集。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>返回值

影响对话框的行为的标志集。

### <a name="remarks"></a>备注

此方法检索的值*uiFlags*传递给构造函数的参数。 返回值可以是一个或多个以下值：

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|允许用户指定卷影菜单的外观。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允许用户指定的文本标签是否显示工具栏按钮图像下方。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允许用户指定的菜单动画样式。  |
|AFX_CUSTOMIZE_NOHELP|从自定义对话框的删除帮助按钮。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|使 WS_EX_CONTEXTHELP 视觉样式。  |
|AFX_CUSTOMIZE_NOTOOLS|移除**工具**自定义对话框中的页。 此标志无效，如果应用程序使用`CUserToolsManager`类。  |
|AFX_CUSTOMIZE_MENUAMPERS|允许按钮标题包含 & 符 ( **&**) 字符。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|移除**大图标**自定义对话框中的选项。  |

WS_EX_CONTEXTHELP 视觉样式的详细信息，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

在发生后立即响应用户工具中的更改。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[in、 out]指向已更改的用户工具对象的指针。

### <a name="remarks"></a>备注

当用户更改的用户定义工具属性时，由框架调用此方法。 默认实现不执行任何操作。 重写此方法在派生类中的`CMFCToolBarsCustomizeDialog`之后发生的更改到的用户工具执行处理。

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

因为用户定义其验证键盘快捷方式。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>参数

*pAccel*<br/>
[in、 out]指向表示为的建议的键盘分配[加速](/windows/desktop/api/winuser/ns-winuser-tagaccel)结构。

### <a name="return-value"></a>返回值

如果该密钥可以是已分配或 FALSE，如果不能分配的密钥，则为 TRUE。 默认实现始终返回 TRUE。

### <a name="remarks"></a>备注

重写此方法在派生类来执行额外的处理时用户将分配新的键盘快捷方式，或以用户身份验证的键盘快捷方式定义它们。 若要防止被分配一个快捷方式，返回 FALSE。 应该还会显示一个消息框或否则通知用户的键盘快捷方式已拒绝的原因。

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

执行自定义处理时对用户工具更改当用户要应用更改时。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>参数

*pSelTool*<br/>
[in、 out]指向要替换的用户工具对象的指针。

### <a name="remarks"></a>备注

将要更改的用户定义工具属性时，由框架调用此方法。 默认实现不执行任何操作。 重写`OnBeforeChangeTool`方法在类中的派生自`CMFCToolBarsCustomizeDialog`如果你想要执行处理之前发生了更改的用户工具，如释放资源的*pSelTool*使用。

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
[in]指向父窗口的指针。

*bitmap*<br/>
[in]对要编辑的位图对象的引用。

*nBitsPerPixel*<br/>
[in]位图颜色分辨率，以每像素位数。

### <a name="return-value"></a>返回值

如果提交的更改; 则为 TRUE否则为 FALSE。 默认实现显示一个对话框，并返回 TRUE，如果用户单击**确定**，或如果用户单击 FALSE**取消**或**关闭**按钮。

### <a name="remarks"></a>备注

用户在运行图像编辑器时，由框架调用此方法。 默认实现显示[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)对话框。 重写`OnEditToolbarMenuImage`派生的类，以使用自定义图像编辑器中。

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

重写以增加属性表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

调用的结果[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。

### <a name="remarks"></a>备注

此方法扩展基类实现[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)，通过显示**关闭**按钮，通过确保对话框的适合当前屏幕大小，以及移动**帮助**对话框左下角的按钮。

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

处理通知框架中的**工具**页是要进行初始化。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写此方法在派生类来处理此通知。

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

在窗口已销毁之后由框架调用。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>备注

此方法扩展的基类实现， `CPropertySheet::PostNcDestroy`，通过还原到以前的模式应用程序。

[CMFCToolBarsCustomizeDialog::Create](#create)方法限制用户访问的自定义任务以特殊模式让应用程序。

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

从指定的类别，或从所有类别中删除具有指定的命令 ID 的按钮。

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
[in]指定要从其中移除按钮的类别 ID。

*uiCmdId*<br/>
[in]指定按钮的命令 ID。

*lpszCategory*<br/>
[in]指定要从其中移除按钮类别的名称。

### <a name="return-value"></a>返回值

删除按钮或如果指定的类别中找不到指定的命令 ID 为-1 的从零开始的索引。 如果*uiCategoryId*为-1，返回值为 0。

### <a name="remarks"></a>备注

若要从所有类别中删除一个按钮，调用此方法，设置的第一个重载*uiCategoryId*为-1。

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

将类别的列表框中的类别上重命名**命令**页。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>参数

*lpszCategoryOld*<br/>
[in]要更改的类别名称。

*lpszCategoryNew*<br/>
[in]新的类别名称。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

类别名称必须是唯一的。

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

将命令的列表框中的工具栏按钮替换上**命令**页。

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
[in]指定要替换为按钮的命令。

*按钮*<br/>
[in]一个**const**替换旧的按钮的工具栏按钮对象的引用。

### <a name="remarks"></a>备注

当[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)， [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)，或[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)添加命令**命令**页上，命令是中的窗体[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象 (或[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)菜单对象包含子菜单添加的项`AddMenuCommands`)。 该框架还会调用这三种方法，以自动添加的命令。 如果你想要改为表示由派生类型的命令，调用`ReplaceButton`和传入的按钮的派生类型。

### <a name="example"></a>示例

下面的示例演示如何使用`ReplaceButton`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

指定在类别列表中的哪些类别上**命令**页是用户类别。 您必须调用此函数，然后再调用[CMFCToolBarsCustomizeDialog::Create](#create)。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>参数

*lpszCategory*<br/>
[in]类别的名称。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

用户类别设置当前未使用框架中。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)
