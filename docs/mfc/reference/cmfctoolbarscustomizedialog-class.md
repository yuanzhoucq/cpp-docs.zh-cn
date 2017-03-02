---
title: "CMFCToolBarsCustomizeDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarsCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog class
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 069498d958dd5d9c3befc2a179c67636ce0ac9ae
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 类
无模式选项卡对话框 ( [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md))，它使用户能够自定义工具栏、 菜单、 键盘快捷方式、 用户定义的工具和应用程序中的视觉样式。 通常，用户可从 **“工具”** 菜单中选择 **“自定义”** 来访问此对话框。  
  
 **自定义**对话框中有六个选项卡︰**命令**，**工具栏**，**工具**，**键盘**，**菜单**，和**选项**。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|构造 `CMFCToolBarsCustomizeDialog` 对象。|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|工具栏按钮将插入命令的列表中上**命令**页|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|从该资源并调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到命令的列表，在**命令**页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|从该资源并调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到命令的列表，在**命令**页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|从资源加载工具栏。 然后，对于每个命令中的菜单调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法插入的命令列表中的按钮上**命令**指定类别下的页。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::Create](#create)|显示**自定义**对话框。|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|留待将来使用。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|启用或禁用通过使用创建新工具栏**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|填充所提供`CListBox`对象中的命令**所有命令**类别。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|填充所提供`CComboBox`对象中每个命令类别同名**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|填充所提供`CListBox`对象中每个命令类别同名**自定义**对话框。|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|检索与给定的命令 ID 相关联的名称|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|检索具有给定的文本标签提供的列表中的项的数目。|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|检索一的组会影响对话框中的行为的标志。|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|启动图像编辑器，以便用户可以自定义工具栏按钮或菜单项图标。|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|重写来扩充属性工作表初始化。 (重写[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|窗口已销毁后，由框架调用。 （重写 `CPropertySheet::PostNcDestroy`。）|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|从指定的类别中，或所有类别，请删除具有指定的命令 ID 的按钮。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|将类别的列表框中的一个类别重命名在**命令**选项卡。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|在替换中的命令列表的按钮**命令**具有新的工具栏按钮对象选项卡。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|将显示在类别列表中添加一个类别**命令**选项卡。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|由框架，以确定是否为有效的用户定义的工具列表调用。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|用户定义的工具的属性更改时由框架调用。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|确定指定的键盘快捷方式是否可以分配给某项操作。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|确定是否可以更改用户定义的工具。|  
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|当用户选择由框架调用**工具**请求选项卡。|  
  
## <a name="remarks"></a>备注  
 若要显示**自定义**对话框框中，创建`CMFCToolBarsCustomizeDialog`对象，并调用[CMFCToolBarsCustomizeDialog::Create](#create)方法。  
  
 虽然**自定义**对话框处于活动状态、 应用程序将限制用户的自定义任务以特殊模式工作。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarsCustomizeDialog`类。 该示例演示如何替换处于命令的列表框中的工具栏按钮上**命令**页上，启用使用创建新工具栏**自定义**对话框中，并显示**自定义**对话框。 此代码段属于[IE 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&4;](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>要求  
 **标头︰** afxToolBarsCustomizeDialog.h  
  
##  <a name="a-nameaddbuttona--cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton  
 工具栏按钮将插入命令的列表中上**命令**页。  
  
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
 指定在其之前插入按钮的工具栏按钮的从零开始索引。  
  
 [in] `lpszCategory`  
 指定要插入按钮的类别字符串。  
  
### <a name="remarks"></a>备注  
 `AddButton`方法将忽略具有标准命令 Id （例如 ID_FILE_MRU_FILE1) 按钮时，不允许的命令 (请参阅[CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虚拟按钮。  
  
 此方法创建具有相同类型的新对象`button`(通常[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)) 通过使用按钮的运行时类。 然后，它调用[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)要复制的数据成员的按钮，并将该副本插入到指定的类别。  
  
 当新建按钮插入时，它会收到`OnAddToCustomizePage`通知。  
  
 如果`iInsertBefore`为-1，按钮追加到类别列表中; 否则它将插入具有指定的索引项的前面。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddButton`方法`CMFCToolBarsCustomizeDialog`类。 此代码段属于[滑块示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Slider #&1;](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="a-nameaddmenua--cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu  
 从该资源并调用加载菜单[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)若要将该菜单添加到命令的列表，在**命令**页。  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiMenuResId`  
 指定要加载一个菜单的资源 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则添加一个菜单否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在调用`AddMenuCommands`，`bPopup`是`FALSE`。 因此，该方法不会添加菜单项包含子菜单命令的列表。 此方法未向命令的列表，在子菜单中添加菜单项。  
  
##  <a name="a-nameaddmenucommandsa--cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands  
 将项添加到列表中的命令**命令**页上，代表指定菜单中的所有项。  
  
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
 要插入菜单上的类别的名称。  
  
 [in] `lpszMenuPath`  
 当该命令显示在添加到的名称的前缀**所有类别**列表。  
  
### <a name="remarks"></a>备注  
 `AddMenuCommands`方法循环访问的所有菜单项`pMenu`。 对于每个不包含子菜单的菜单项，此方法会创建[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象并调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将菜单项作为工具栏按钮添加到命令的列表，在**命令**页。 在此过程中，分隔符将被忽略。  
  
 如果`bPopup`是`TRUE`，每个菜单项包含子菜单，此方法创建[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并将其插入到的命令列表，通过调用`AddButton`。 否则，包含子菜单的菜单项不会显示在命令的列表中。 在任一情况下，当`AddMenuCommands`遇到菜单项在子菜单调用其自身以递归方式，将指针传递给作为子菜单`pMenu`参数并追加到的子菜单中的标签`lpszMenuPath`。  
  
##  <a name="a-nameaddtoolbara--cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar  
 从资源加载工具栏。 然后，对于每个命令中的菜单调用[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法插入的命令列表中的按钮上**命令**指定类别下的页。  
  
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
 指定的命令列表中插入其命令工具栏上的资源 ID。  
  
 [in] `lpszCategory`  
 指定要向其中添加工具栏的类别的名称。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddToolBar`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码段属于[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&11;](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>备注  
 用于表示每个命令的控件是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。 添加工具栏后，您可以将按钮与派生类型的控件通过调用[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)。  
  
##  <a name="a-namechecktoolsvaliditya--cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 验证的用户工具列表的有效性。  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>参数  
 [in] `lstTools`  
 用户定义的工具来检查的列表。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`的用户定义的工具列表是否有效; 否则为`FALSE`。 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法以验证表示用户定义的工具，通过返回的对象的有效性[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)。  
  
 重写`CheckToolsValidity`方法在类派生自`CMFCToolBarsCustomizeDialog`如果想要在用户关闭对话框前验证的用户工具。 如果此方法返回`FALSE`时用户将单击**关闭**右上角中的对话框或标记为按钮的按钮**关闭**对话框中显示在对话框中的右下角，**工具**而不是关闭的选项卡。 如果此方法返回`FALSE`当用户单击选项卡以离开**工具**选项卡上，导航不会发生。 应显示相应的消息框以通知用户导致验证失败的问题。  
  
##  <a name="a-namecmfctoolbarscustomizedialoga--cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
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
 指向与父框架的指针。 此参数不能为 `NULL`。  
  
 [in] `bAutoSetFromMenus`  
 一个布尔值，指定是否将菜单命令从所有菜单添加到命令的列表，在**命令**页。 如果此参数为`TRUE`，添加的菜单命令。 否则，不会添加的菜单命令。  
  
 [in] `uiFlags`  
 影响对话框中的行为的标志的组合。 此参数可以为一个或多个下列值︰  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [in] `plistCustomPages`  
 指向的列表的指针`CRuntimeClass`指定附加的自定义页的对象。  
  
### <a name="remarks"></a>备注  
 `plistCustomPages`参数引用的列表`CRuntimeClass`指定附加的自定义页的对象。 构造函数添加到对话框中更多的页通过使用[CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法。 请参阅有关的示例，将添加到更多的页 CustomPages 示例**自定义**对话框。  
  
 有关可以传入的值的详细信息`uiFlags`参数，请参阅[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCToolBarsCustomizeDialog`类。 此代码段属于[的自定义页示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages #&3;](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="a-namecreatea--cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFCToolBarsCustomizeDialog::Create  
 显示**自定义**对话框。  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建自定义属性表否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用`Create`方法只在完全初始化类之后。  
  
##  <a name="a-nameenableuserdefinedtoolbarsa--cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 启用或禁用通过使用创建新工具栏**自定义**对话框。  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用用户定义的工具栏。`FALSE`禁用工具栏。  
  
### <a name="remarks"></a>备注  
 如果`bEnable`是`TRUE`、**新建**，**重命名**和**删除**中显示的按钮**工具栏**页。  
  
 默认情况下，或者如果`bEnable`是`FALSE`，这些按钮不会显示，并且用户不能定义新的工具栏。  
  
##  <a name="a-namefillallcommandslista--cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 填充所提供`CListBox`对象中的命令**所有命令**类别。  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `wndListOfCommands`  
 对引用`CListBox`要填充对象。  
  
### <a name="remarks"></a>备注  
 **所有命令**类别包含的所有类别的命令。 [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法将添加到提供的按钮与相关联的命令**所有命令**为您的类别。  
  
 此方法会清除所提供的内容`CListBox`之前使用中的命令对其进行填充对象**所有命令**类别。  
  
 `CMFCMousePropertyPage`类使用此方法来填充双击事件列表框。  
  
##  <a name="a-namefillcategoriescomboboxa--cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
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
 一个布尔值，该值指定是否将类别添加到不具有命令的组合框。 如果此参数为`TRUE`，空类别添加到组合框。 否则，不会添加空的类别。  
  
### <a name="remarks"></a>备注  
 此方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)方法之处在于此方法适用于`CComboBox`对象。  
  
 此方法不会清除的内容`CComboBox`之前对其进行填充的对象。 它可保证**所有命令**类别是组合框中的最后一个项目。  
  
 您可以通过添加新命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 可以通过更改现有类别的名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`类使用此方法来对其进行分类的键盘映射。  
  
##  <a name="a-namefillcategorieslistboxa--cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
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
 一个布尔值，该值指定是否将类别添加到不具有命令列表框中。 如果此参数为`TRUE`，空类别添加到列表框中。 否则，不会添加空的类别。  
  
### <a name="remarks"></a>备注  
 此方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)方法之处在于此方法适用于`CListBox`对象。  
  
 此方法不会清除的内容`CListBox`之前对其进行填充的对象。 它可保证**所有命令**类别是在列表框中的最后一个项目。  
  
 您可以通过添加新命令类别[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 可以通过更改现有类别的名称[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsCommandsPropertyPage`类使用此方法以显示与每个命令类别相关联的命令列表。  
  
##  <a name="a-namegetcommandnamea--cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName  
 检索与给定的命令 ID 相关联的名称  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 要检索的命令 ID。  
  
### <a name="return-value"></a>返回值  
 与给定的命令 ID 相关联的名称或`NULL`如果该命令不存在。  
  
##  <a name="a-namegetcountincategorya--cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory  
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
 参考列表，其中包含`CMFCToolBarButton`对象。  
  
### <a name="return-value"></a>返回值  
 在提供的项目数列表等于文本标签`lpszItemName`。  
  
### <a name="remarks"></a>备注  
 提供的对象列表中每个元素必须属于类型`CMFCToolBarButton`。 此方法比较`lpszItemName`与[CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)数据成员。  
  
##  <a name="a-namegetflagsa--cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags  
 检索一的组会影响对话框中的行为的标志。  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>返回值  
 这组会影响对话框中的行为的标志。  
  
### <a name="remarks"></a>备注  
 此方法检索的值`uiFlags`传递给构造函数的参数。 返回值可以是一个或多个下列值︰  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 允许用户指定菜单上的卷影外观。  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 允许用户指定是否将工具栏按钮图像的下方显示的文本标签。  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 允许用户指定菜单动画样式。  
  
 `AFX_CUSTOMIZE_NOHELP`  
 删除自定义对话框中的帮助按钮。  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 使`WS_EX_CONTEXTHELP`视觉样式。  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 删除**工具**从自定义对话框中的页。 此标志无效，如果您的应用程序使用`CUserToolsManager`类。  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 允许按钮标题包含 & 符 ( ** & **) 字符。  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 删除**大图标**从自定义对话框中的选项。  
  
 有关详细信息`WS_EX_CONTEXTHELP`视觉样式，请参阅[扩展窗口样式](../../mfc/reference/extended-window-styles.md)。  
  
##  <a name="a-nameonafterchangetoola--cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 它发生后立即响应用户工具中的更改。  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pSelTool`  
 指向已更改的用户工具对象的指针。  
  
### <a name="remarks"></a>备注  
 当用户更改用户定义的工具的属性时，将由框架调用此方法。 默认实现不执行任何操作。 重写此方法在派生类中的`CMFCToolBarsCustomizeDialog`之后发生更改的用户工具执行处理。  
  
##  <a name="a-nameonassignkeya--cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey  
 验证键盘快捷方式，如用户定义它们。  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pAccel`  
 指针指向表示为建议的键盘分配[加速](http://msdn.microsoft.com/library/windows/desktop/ms646340)结构。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以分配键，或`FALSE`如果无法分配给该密钥。 默认实现始终返回`TRUE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来执行额外处理，当用户将分配新的键盘快捷键，或以用户身份验证的键盘快捷方式定义它们。 若要防止指派一个快捷方式，返回`FALSE`。 您应该还显示一个消息框或否则通知给用户的键盘快捷方式已拒绝的原因。  
  
##  <a name="a-nameonbeforechangetoola--cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 执行自定义处理时对用户工具更改用户将要应用更改时。  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pSelTool`  
 指向要被替换的用户工具对象的指针。  
  
### <a name="remarks"></a>备注  
 要更改用户定义的工具的属性时，将由框架调用此方法。 默认实现不执行任何操作。 重写`OnBeforeChangeTool`方法在类派生自`CMFCToolBarsCustomizeDialog`如果想要执行处理在发生更改的用户工具，如释放资源之前，`pSelTool`使用。  
  
##  <a name="a-nameonedittoolbarmenuimagea--cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
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
 对要编辑一个位图对象的引用。  
  
 [in] `nBitsPerPixel`  
 用于颜色分辨率，以位 / 像素的位图。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果提交的更改;，否则为`FALSE`。 默认实现显示一个对话框，并返回`TRUE`如果用户单击**确定**，或`FALSE`如果用户单击**取消**或**关闭**按钮。  
  
### <a name="remarks"></a>备注  
 当用户运行图像编辑器时，将由框架调用此方法。 默认实现显示[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)对话框。 重写`OnEditToolbarMenuImage`派生类以使用自定义图像编辑器中。  
  
##  <a name="a-nameoninitdialoga--cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog  
 重写来扩充属性工作表初始化。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 因调用[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)，通过显示**关闭**按钮，以确保能满足当前的屏幕尺寸、 的对话框中，然后将移动**帮助**对话框的左下角的按钮。  
  
##  <a name="a-nameoninittoolspagea--cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 处理来自该框架的通知，**工具**页是要进行初始化。  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 重写此方法在派生类来处理此通知。  
  
##  <a name="a-namepostncdestroya--cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy  
 窗口已销毁后，由框架调用。  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， `CPropertySheet::PostNcDestroy`，通过将还原到以前的模式的应用程序。  
  
 [CMFCToolBarsCustomizeDialog::Create](#create)方法将限制用户的自定义任务以特殊模式将应用程序。  
  
##  <a name="a-nameremovebuttona--cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton  
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
 指定要从中移除按钮的类别 ID。  
  
 [in] `uiCmdId`  
 指定按钮的命令 ID。  
  
 [in] `lpszCategory`  
 指定要从中移除按钮类别的名称。  
  
### <a name="return-value"></a>返回值  
 删除按钮，否则为-1 指定的类别中找不到指定的命令 ID 的从零开始的索引。 如果`uiCategoryId`为-1，返回值为 0。  
  
### <a name="remarks"></a>备注  
 若要从所有类别中删除一个按钮，调用此方法并集的第一个重载`uiCategoryId`为-1。  
  
##  <a name="a-namerenamecategorya--cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::RenameCategory  
 将类别的列表框中的一个类别重命名在**命令**页。  
  
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
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 类别名称必须是唯一的。  
  
##  <a name="a-namereplacebuttona--cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton  
 将命令的列表框中的工具栏按钮替换上**命令**页。  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 指定要替换为按钮的命令。  
  
 [in] `button`  
 一个`const`替换旧的按钮的工具栏按钮对象引用。  
  
### <a name="remarks"></a>备注  
 当[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)， [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)，或[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)添加到命令**命令**页上，命令的形式是[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象 (或[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)菜单项包含子菜单添加对象`AddMenuCommands`)。 框架还将调用这三种方法，以自动添加的命令。 如果您想要表示由派生类型的命令，调用`ReplaceButton`，然后将传入的按钮的派生类型。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`ReplaceButton`中的方法`CMFCToolBarsCustomizeDialog`类。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&34;](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="a-namesetusercategorya--cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUserCategory  
 指定的类别列表中的哪些类别上**命令**页是用户类别。 您必须在调用之前调用此函数[CMFCToolBarsCustomizeDialog::Create](#create)。  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCategory`  
 类别的名称。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 用户类别设置当前未使用由框架中。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)

