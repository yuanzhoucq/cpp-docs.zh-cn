---
title: "CMFCToolBarsCustomizeDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 978303c9edaec2d9776d6e1c81b530df791ca5ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 类
无模式选项卡对话框 ( [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md))，使用户能够自定义工具栏、 菜单、 键盘快捷键、 用户定义的工具和应用程序中的视觉样式。 通常，用户可从 **“工具”** 菜单中选择 **“自定义”** 来访问此对话框。  
  
 **自定义**对话框中有六个选项卡：**命令**，**工具栏**，**工具**，**键盘**， **菜单**，和**选项**。  
  
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
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|将插入的命令的列表上的工具栏按钮**命令**页|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到的命令的列表中上,**命令**页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到的命令的列表中上,**命令**页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|从资源加载工具栏。 然后，为每个命令中的菜单调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法上插入的命令的列表中的按钮**命令**指定类别下的页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::Create](#create)|显示**自定义**对话框。|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|留待将来使用。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|启用或禁用通过使用创建新工具栏**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|填充所提供`CListBox`对象中的命令**所有命令**类别。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|填充所提供`CComboBox`对象中每个命令类别同名**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|填充所提供`CListBox`对象中每个命令类别同名**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|检索与给定的命令 ID 相关联的名称|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|检索具有给定的文本标签提供的列表中的项的数目。|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|检索组的影响的对话框中的行为的标志。|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|替代来增加属性表初始化。 (重写[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|在窗口已销毁之后由框架调用。 （重写 `CPropertySheet::PostNcDestroy`。）|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|从指定的类别中，或所有类别，请删除具有指定的命令 ID 的按钮。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|将类别的列表框中的类别上重命名**命令**选项卡。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|在替换中的命令的列表的按钮**命令**与新的工具栏按钮对象的选项卡。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|将显示在类别列表中添加一个类别**命令**选项卡。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|由框架调用以确定是否为有效的用户定义的工具列表。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|用户定义的工具的属性更改时由框架调用。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|确定指定的键盘快捷方式是否可以分配给某项操作。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|确定是否可以更改用户定义的工具。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|由框架调用，当用户选择**工具**请求选项卡。|  
  
## <a name="remarks"></a>备注  
 若要显示**自定义**对话框框中，创建`CMFCToolBarsCustomizeDialog`对象并调用[CMFCToolBarsCustomizeDialog::Create](#create)方法。  
  
 虽然**自定义**对话框中处于活动状态，该应用程序有效限制用户访问的自定义任务以特殊模式。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarsCustomizeDialog`类。 该示例演示如何将命令的列表框中的工具栏按钮上**命令**页上，启用通过使用创建新工具栏**自定义**对话框中，并显示**自定义**对话框。 此代码片段属于[IE 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>惠?  
 **标头：** afxToolBarsCustomizeDialog.h  
  
##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton  
 将插入的命令的列表上的工具栏按钮**命令**页。  
  
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
 [in] `uiCategoryId`  
 指定要将按钮插入到其中的类别 ID。  
  
 [in] `button`  
 指定要插入的按钮。  
  
 [in] `iInsertBefore`  
 指定在其前插入该按钮的工具栏按钮的从零开始索引。  
  
 [in] `lpszCategory`  
 指定要插入的按钮的类别字符串。  
  
### <a name="remarks"></a>备注  
 `AddButton`方法将忽略具有标准命令 Id （如 ID_FILE_MRU_FILE1) 的按钮时，不允许的命令 (请参阅[CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虚拟按钮。  
  
 此方法创建具有相同类型的新对象`button`(通常[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)) 通过使用运行时类的按钮。 然后，它调用[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)来复制按钮，数据成员并将该副本插入到指定的类别。  
  
 当新建按钮将插入时，它会收到`OnAddToCustomizePage`通知。  
  
 如果`iInsertBefore`为-1，按钮追加到类别列表中; 否则它将插入到具有指定索引的项的前面。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddButton`方法`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[滑块示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu  
 从资源和调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到的命令的列表中上,**命令**页。  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiMenuResId`  
 指定要加载一个菜单的资源 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则添加到菜单否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在调用`AddMenuCommands`，`bPopup`是`FALSE`。 因此，该方法不会添加包含向的命令列表的子菜单的菜单项。 此方法未添加菜单项在子菜单中的命令的列表。  
  
##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands  
 将项添加到列表中的命令**命令**页后，可以表示指定的菜单中的所有项。  
  
```  
void AddMenuCommands(
    const CMenu* pMenu,  
    BOOL bPopup,  
    LPCTSTR lpszCategory=NULL,  
    LPCTSTR lpszMenuPath=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenu`  
 指向要添加的 CMenu 对象的指针。  
  
 [in] `bPopup`  
 指定是否要插入到列表的命令的弹出菜单项。  
  
 [in] `lpszCategory`  
 要将菜单插入的类别的名称。  
  
 [in] `lpszMenuPath`  
 在中显示该命令时添加到的名称的前缀**所有类别**列表。  
  
### <a name="remarks"></a>备注  
 `AddMenuCommands`方法循环访问的所有菜单项`pMenu`。 为每个不包含子菜单的菜单项，此方法创建[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象并调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将作为工具栏添加菜单项按钮上的命令的列表**命令**页。 在此过程中，分隔符将被忽略。  
  
 如果`bPopup`是`TRUE`，对于每个菜单项包含子菜单，此方法创建[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并将其插入到的命令的列表，通过调用`AddButton`。 否则包含子菜单的菜单项不会显示在的命令的列表中。 在任一情况下，当`AddMenuCommands`遇到菜单项与子菜单它本身以递归方式调用，将指针传递给为子菜单`pMenu`参数并将追加到子菜单的标签`lpszMenuPath`。  
  
##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar  
 从资源加载工具栏。 然后，为每个命令中的菜单调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法上插入的命令的列表中的按钮**命令**指定类别下的页。  
  
```  
BOOL AddToolBar(
    UINT uiCategoryId,  
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,  
    UINT uiToolbarResId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCategoryId`  
 指定要添加到工具栏类别的资源 ID。  
  
 [in] `uiToolbarResId`  
 指定的命令的列表中插入其命令工具栏的资源 ID。  
  
 [in] `lpszCategory`  
 指定要向其中添加工具栏类别的名称。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddToolBar`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>备注  
 用于表示每个命令的控件是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。 添加工具栏后，您可以将按钮与派生类型的控件通过调用[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)。  
  
##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 验证用户工具列表中的有效性。  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>参数  
 [in] `lstTools`  
 用户定义的工具来检查的列表。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`的用户定义的工具列表是否有效; 否则为`FALSE`。 默认实现始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 框架在调用此方法以验证表示用户定义的工具，通过返回的对象的有效性[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)。  
  
 重写`CheckToolsValidity`从派生类中的方法`CMFCToolBarsCustomizeDialog`如果你想要验证的用户工具之前用户关闭对话框。 如果此方法返回`FALSE`当用户单击任一**关闭**右上角的对话框中或标记的按钮按钮**关闭**右下角的对话框中，对话框中显示**工具**而不是关闭的选项卡。 如果此方法返回`FALSE`当用户单击选项卡以导航离开**工具**选项卡上，在导航窗格不会发生。 应显示适当的消息框，通知用户导致验证失败的问题。  
  
##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
 构造 `CMFCToolBarsCustomizeDialog` 对象。  
  
```  
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bAutoSetFromMenus = FALSE,  
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),  
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParentFrame`  
 指向的父框架的指针。 此参数不能为 `NULL`。  
  
 [in] `bAutoSetFromMenus`  
 一个布尔值，指定是否将菜单命令从所有菜单添加到的命令的列表上,**命令**页。 如果此参数为`TRUE`，添加菜单命令。 否则，不会添加菜单命令。  
  
 [in] `uiFlags`  
 影响对话框中的行为的标志的组合。 此参数可以为一个或多个以下值：  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [in] `plistCustomPages`  
 指针的列表`CRuntimeClass`指定其他自定义页的对象。  
  
### <a name="remarks"></a>备注  
 `plistCustomPages`参数指的列表`CRuntimeClass`指定其他自定义页的对象。 构造函数通过使用向对话框添加更多的页[CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法。 请参阅有关的示例，将添加到的更多页 CustomPages 示例**自定义**对话框。  
  
 有关可以传入的值的详细信息`uiFlags`参数，请参阅[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[自定义页示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="create"></a>CMFCToolBarsCustomizeDialog::Create  
 显示**自定义**对话框。  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建自定义属性表否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用`Create`仅后完全初始化类的方法。  
  
##  <a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 启用或禁用通过使用创建新工具栏**自定义**对话框。  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用用户定义的工具栏;`FALSE`禁用工具栏。  
  
### <a name="remarks"></a>备注  
 如果`bEnable`是`TRUE`、**新建**，**重命名**和**删除**上显示按钮**工具栏**页。  
  
 默认情况下，或者如果`bEnable`是`FALSE`，这些按钮不会显示，并且用户不能定义新工具栏。  
  
##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 填充所提供`CListBox`对象中的命令**所有命令**类别。  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `wndListOfCommands`  
 对引用`CListBox`要填充对象。  
  
### <a name="remarks"></a>备注  
 **所有命令**类别包含的所有类别的命令。 [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将添加到提供的按钮与关联的命令**所有命令**为你的类别。  
  
 此方法清除的内容提供`CListBox`之前填充与中的命令对象**所有命令**类别。  
  
 `CMFCMousePropertyPage`类使用此方法以填充双击事件列表框。  
  
##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
 填充所提供`CComboBox`对象中每个命令类别同名**自定义**对话框。  
  
```  
void FillCategoriesComboBox(
    CComboBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `wndCategory`  
 对引用`CComboBox`要填充对象。  
  
 [in] `bAddEmpty`  
 一个布尔值，指定是否将类别添加到不具有命令的组合框。 如果此参数为`TRUE`，空的类别添加到组合框。 否则，不会添加空的类别。  
  
### <a name="remarks"></a>备注  
 此方法就像是[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)方法只不过此方法适用于`CComboBox`对象。  
  
 此方法并不会清除的内容`CComboBox`之前填充它的对象。 它可保证**所有命令**类别是组合框中的最后一项。  
  
 你可以通过添加新命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 你可以通过使用更改的现有类别名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`类使用此方法进行分类键盘映射。  
  
##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
 填充所提供`CListBox`对象中每个命令类别同名**自定义**对话框。  
  
```  
void FillCategoriesListBox(
    CListBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `wndCategory`  
 对引用`CListBox`要填充对象。  
  
 [in] `bAddEmpty`  
 一个布尔值，指定是否将类别添加到不具有命令的列表框。 如果此参数为`TRUE`，空的类别添加到列表框中。 否则，不会添加空的类别。  
  
### <a name="remarks"></a>备注  
 此方法就像是[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)方法只不过此方法适用于`CListBox`对象。  
  
 此方法并不会清除的内容`CListBox`之前填充它的对象。 它可保证**所有命令**类别是列表框中的最后一项。  
  
 你可以通过添加新命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 你可以通过使用更改的现有类别名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsCommandsPropertyPage`类使用此方法以显示与每个命令类别关联的命令的列表。  
  
##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName  
 检索与给定的命令 ID 相关联的名称  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 要检索的命令 ID。  
  
### <a name="return-value"></a>返回值  
 与给定的命令 ID，相关联的名称或`NULL`如果不存在的命令。  
  
##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory  
 检索具有给定的文本标签提供的列表中的项的数目。  
  
```  
int GetCountInCategory(
    LPCTSTR lpszItemName,  
    const CObList& lstCommands) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszItemName`  
 要匹配的文本标签。  
  
 [in] `lstCommands`  
 对包含的列表的引用`CMFCToolBarButton`对象。  
  
### <a name="return-value"></a>返回值  
 在提供的项的数目列出其文本标签等于`lpszItemName`。  
  
### <a name="remarks"></a>备注  
 提供的对象列表中每个元素必须属于类型`CMFCToolBarButton`。 此方法比较`lpszItemName`与[CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)数据成员。  
  
##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags  
 检索组的影响的对话框中的行为的标志。  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>返回值  
 这组影响的对话框中的行为的标志。  
  
### <a name="remarks"></a>备注  
 此方法检索的值`uiFlags`传递给构造函数的参数。 返回值可以是一个或多个以下值：  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 允许用户指定卷影菜单的外观。  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 允许用户可以指定是否显示工具栏按钮图像下方的文本标签。  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 允许用户指定菜单动画样式。  
  
 `AFX_CUSTOMIZE_NOHELP`  
 移除自定义对话框中的帮助按钮。  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 使`WS_EX_CONTEXTHELP`视觉样式。  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 删除**工具**从自定义对话框中的页。 此标志是如果你的应用程序使用有效`CUserToolsManager`类。  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 允许按钮标题，以包含 & 符 (  **&** ) 字符。  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 删除**大图标**从自定义对话框中的选项。  
  
 有关详细信息`WS_EX_CONTEXTHELP`视觉样式，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。  
  
##  <a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 发生后立即响应用户工具中的更改。  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pSelTool`  
 指向已更改的用户工具对象的指针。  
  
### <a name="remarks"></a>备注  
 用户更改的用户定义的工具的属性时，将由框架调用此方法。 默认实现不执行任何操作。 重写此方法在派生类的`CMFCToolBarsCustomizeDialog`以执行处理后发生更改的用户工具。  
  
##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey  
 验证键盘快捷方式，因为用户定义它们。  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pAccel`  
 指向表示为的建议的键盘分配[加速](http://msdn.microsoft.com/library/windows/desktop/ms646340)结构。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以分配的密钥，或`FALSE`如果无法分配密钥。 默认实现始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类以执行额外的处理时用户将分配一个新的键盘快捷方式，或以用户身份验证的键盘快捷方式定义它们。 若要防止对指派快捷方式，返回`FALSE`。 你应还显示一个消息框或否则通知给用户的键盘快捷方式为何被拒绝的原因。  
  
##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 执行自定义处理到一个用户工具出现更改时用户将要应用更改时。  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pSelTool`  
 指向要替换的用户工具对象的指针。  
  
### <a name="remarks"></a>备注  
 将要更改的用户定义的工具的属性时，将由框架调用此方法。 默认实现不执行任何操作。 重写`OnBeforeChangeTool`从派生类中的方法`CMFCToolBarsCustomizeDialog`如果你想要执行处理之前发生更改的用户工具，如释放资源，`pSelTool`使用。  
  
##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
 启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。  
  
```  
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,  
    CBitmap& bitmap,  
    int nBitsPerPixel);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向父窗口的指针。  
  
 [in] `bitmap`  
 对用于进行编辑的位图的对象的引用。  
  
 [in] `nBitsPerPixel`  
 Bitmap 颜色分辨率，以每像素位数。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果提交的更改;，否则为`FALSE`。 默认实现显示一个对话框，并返回`TRUE`如果用户单击**确定**，或`FALSE`如果用户单击**取消**或**关闭**按钮。  
  
### <a name="remarks"></a>备注  
 用户在运行图像编辑器时，将由框架调用此方法。 默认实现显示[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)对话框。 重写`OnEditToolbarMenuImage`派生的类，以使用自定义图像编辑器中。  
  
##  <a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog  
 替代来增加属性表初始化。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 调用[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。  
  
### <a name="remarks"></a>备注  
 此方法扩展的基类实现， [cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)，通过显示**关闭**按钮，以确保能满足当前屏幕的大小的对话框中，然后将移动**帮助**到对话框中的左下角的按钮。  
  
##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 处理从框架通知，**工具**页即将进行初始化。  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 重写此方法在派生类来处理此通知。  
  
##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy  
 在窗口已销毁之后由框架调用。  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>备注  
 此方法扩展的基类实现， `CPropertySheet::PostNcDestroy`，通过还原到以前的模式应用程序。  
  
 [CMFCToolBarsCustomizeDialog::Create](#create)方法将限制用户访问的自定义任务以特殊模式的应用程序。  
  
##  <a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton  
 从指定的类别中，或所有类别，请删除具有指定的命令 ID 的按钮。  
  
```  
int RemoveButton(
    UINT uiCategoryId,  
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,  
    UINT uiCmdId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCategoryId`  
 指定要从中删除该按钮的类别 ID。  
  
 [in] `uiCmdId`  
 指定按钮的命令 ID。  
  
 [in] `lpszCategory`  
 指定要从中删除按钮类别的名称。  
  
### <a name="return-value"></a>返回值  
 删除按钮，则为-1 如果指定类别中找不到指定的命令 ID 的从零开始的索引。 如果`uiCategoryId`为-1，返回值为 0。  
  
### <a name="remarks"></a>备注  
 若要删除所有类别的某个按钮，调用此方法和组的第一个重载`uiCategoryId`为-1。  
  
##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory  
 将类别的列表框中的类别上重命名**命令**页。  
  
```  
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,  
    LPCTSTR lpszCategoryNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCategoryOld`  
 要更改的类别名称。  
  
 [in] `lpszCategoryNew`  
 新的类别名称。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 类别名称必须是唯一的。  
  
##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton  
 替换命令的列表框中的工具栏按钮上**命令**页。  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 指定要替换为按钮的命令。  
  
 [in] `button`  
 A`const`替换旧的按钮的工具栏按钮对象引用。  
  
### <a name="remarks"></a>备注  
 当[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)， [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)，或[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)添加命令**命令**页上，命令采用的形式[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象 (或[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)菜单对象包含子菜单添加的项`AddMenuCommands`)。 框架还会调用这三种方法，以自动添加命令。 如果你想要改为表示由派生类型的命令，调用`ReplaceButton`，然后将传入的按钮的派生类型。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`ReplaceButton`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory  
 指定的类别列表中的哪些类别上**命令**页是用户类别。 您必须调用此函数，然后才能调用[CMFCToolBarsCustomizeDialog::Create](#create)。  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCategory`  
 类别的名称。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架当前不使用用户类别设置。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)
