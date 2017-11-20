---
title: "CMouseManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
dev_langs: C++
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e395596ee8decde683c13c12a0c1f2bd33a8cc58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmousemanager-class"></a>CMouseManager 类
允许用户将不同的命令与特定相关联[CView](../../mfc/reference/cview-class.md)当用户在视图内双击对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|将添加`CView`对象传递给**自定义**对话框。 **自定义**对话框中，用户可以将一次双击与命令相关联的每个列出的视图。|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|返回在提供的视图内双击时执行的命令。|  
|[CMouseManager::GetViewIconId](#getviewiconid)|返回与提供的视图 id。 关联的图标|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|返回与提供的视图名称关联的视图 ID。|  
|[CMouseManager::GetViewNames](#getviewnames)|检索所有添加的视图名称的列表。|  
|[CMouseManager::LoadState](#loadstate)|加载`CMouseManager`状态从 Windows 注册表。|  
|[CMouseManager::SaveState](#savestate)|写入`CMouseManager`状态的 Windows 注册表。|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|将提供的命令以及提供的视图相关联。|  
  
## <a name="remarks"></a>备注  
 `CMouseManager`类维护一套`CView`对象。 每个视图被标识由一个名称并且由一个 id。 这些视图所示**自定义**对话框。 用户可以更改为与通过任何视图关联的命令**自定义**对话框。 当用户双击该视图中执行关联的命令。 若要从编码的角度来看支持此功能，必须处理`WM_LBUTTONDBLCLK`消息并调用[CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)此代码中的函数`CView`对象...  
  
 不应创建`CMouseManager`手动对象。 它将由你的应用程序的框架创建。 它将也会自动销毁时在用户退出应用程序。 若要获取指向鼠标管理器为你的应用程序的指针，调用[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmousemanager.h  
  
##  <a name="addview"></a>CMouseManager::AddView  
 注册[CView](../../mfc/reference/cview-class.md)对象[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)以支持自定义鼠标行为。  
  
```  
BOOL AddView(
    int iViewId,  
    UINT uiViewNameResId,  
    UINT uiIconId = 0);

 
BOOL AddView(
    int iId,  
    LPCTSTR lpszViewName,  
    UINT uiIconId = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `iViewId`  
 视图 id。  
  
 [in] `uiViewNameResId`  
 引用的视图名称的资源字符串 ID。  
  
 [in] `uiIconId`  
 视图图标 id。  
  
 [in] `iId`  
 视图 id。  
  
 [in] `lpszViewName`  
 视图名称。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 为了支持自定义鼠标行为，必须向注册视图`CMouseManager`对象。 任何对象派生自`CView`类可注册到鼠标管理器。 字符串和与视图关联的图标显示在**鼠标**选项卡**自定义**对话框。  
  
 它负责程序员也要创建和维护视图 Id 如`iViewId`和`iId`。  
  
 有关如何提供自定义鼠标行为的详细信息，请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何检索一个指向`CMouseManager`通过使用对象`CWinAppEx::GetMouseManager`方法和`AddView`中的方法`CMouseManager`类。 此代码片段属于[状态收集样本](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 返回在提供的视图内双击时执行的命令。  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iId`  
 视图 id。  
  
### <a name="return-value"></a>返回值  
 如果视图是与命令; 关联的命令标识符否则为 0。  
  
##  <a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 检索与视图 id。 关联的图标  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iViewId`  
 视图 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则一个图标资源标识符否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法将失败，如果通过使用未首先注册视图[CMouseManager::AddView](#addview)。  
  
##  <a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 检索与视图名称关联的视图 ID。  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 视图名称。  
  
### <a name="return-value"></a>返回值  
 如果成功，则视图 ID否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法搜索通过使用注册的视图[CMouseManager::AddView](#addview)。  
  
##  <a name="getviewnames"></a>CMouseManager::GetViewNames  
 检索的所有已注册的视图名称的列表。  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `listOfNames`  
 对引用`CStringList`对象。  
  
### <a name="remarks"></a>备注  
 此方法填充参数`listOfNames`使用注册的所有视图的名称与[CMouseManager::AddView](#addview)。  
  
##  <a name="loadstate"></a>CMouseManager::LoadState  
 加载的状态[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)注册表中。  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从注册表加载的状态信息包括已注册的视图、 视图标识符和关联的命令。 如果参数`lpszProfileName`是`NULL`，此函数加载`CMouseManager`控制的默认注册表位置中的数据[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。  
  
 在大多数情况下，无需直接调用此函数。 它是作为工作区中初始化过程的一部分调用。 有关工作区中初始化过程的详细信息，请参阅[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。  
  
##  <a name="savestate"></a>CMouseManager::SaveState  
 写入的状态[CMouseManager 类](../../mfc/reference/cmousemanager-class.md)到注册表。  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 写入注册表的状态信息包括所有已注册的视图、 查看标识符和关联的命令。 如果参数`lpszProfileName`是`NULL`，此函数会写入`CMouseManager`数据由控制的默认注册表位置[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。  
  
 在大多数情况下，无需直接调用此函数。 它是作为工作区中序列化过程的一部分调用。 有关工作区中序列化过程的详细信息，请参阅[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
##  <a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 将自定义命令与首次注册到鼠标管理器的视图相关联。  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `iViewId`  
 视图标识符。  
  
 [in] `uiCmd`  
 命令标识符中。  
  
### <a name="remarks"></a>备注  
 为了将自定义命令关联的视图，你必须先注册视图通过使用[CMouseManager::AddView](#addview)。 `AddView`方法需要的视图标识符作为输入参数。 一旦你注册一个视图，就可以调用`CMouseManager::SetCommandForDblClk`相同视图标识符输入参数提供给`AddView`。 此后，当用户双击鼠标中已注册的视图，应用程序将执行命令由`uiCmd.`以支持自定义鼠标行为，你将还需要自定义注册到鼠标管理器的视图。 有关自定义鼠标行为的详细信息，请参阅 [键盘和鼠标自定义]--brokenlink-(.../ 鼠标和键盘 customization.md）。  
  
 如果`uiCmd`设置为 0，指定的视图已不再与命令关联。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)   
 [键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)



