---
title: CKeyboardManager 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
dev_langs:
- C++
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27ff8f622eb3af52ad23f8f4fc7a20ecb8be9b77
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041131"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 类
管理主框架窗口和子框架窗口的快捷键表。  
  
## <a name="syntax"></a>语法  
  
```  
class CKeyboardManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|构造 `CKeyboardManager` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CKeyboardManager::CleanUp](#cleanup)|清除的快捷键表。|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|检索指定的命令和窗口的默认快捷键。|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|确定是否由快捷键对应表处理一个键。|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|指示是否可打印字符。|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|该值指示菜单显示所有命令的键盘快捷方式或默认快捷键。|  
|[CKeyboardManager::LoadState](#loadstate)|从 Windows 注册表中加载的快捷键表。|  
|[CKeyboardManager::ResetAll](#resetall)|将重新加载的快捷键表从应用程序资源。|  
|[CKeyboardManager::SaveState](#savestate)|将快捷方式表保存到 Windows 注册表中。|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定框架显示所有命令的所有快捷键或每个命令的单个快捷键。 此方法不会影响具有只有一个关联的快捷键的命令。|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|将字符转换为其上限的注册。|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|使用新的快捷方式键表中更新快捷键表。|  
  
## <a name="remarks"></a>备注  
 此类的成员，可以保存和加载到 Windows 注册表的快捷键表，使用模板来更新快捷方式表，并在框架窗口中查找命令的默认快捷键。 此外，`CKeyboardManager`对象，可以控制如何向用户显示键盘快捷方式。  
  
 不应创建`CKeyboardManager`手动对象。 它将由你的应用程序的框架自动创建。 但是，你应调用[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)在初始化过程中你的应用程序。 若要获取指向键盘管理器为你的应用程序的指针，调用[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索一个指向`CKeyboardManager`对象`CWinAppEx`类，以及如何显示所有相关联的快捷键与菜单命令。 此代码片段属于[自定义页示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxkeyboardmanager.h  
  
##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager  
 构造 `CKeyboardManager` 对象。  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，你不必创建`CKeyboardManager`直接。 默认情况下，框架会自动进行创建。 若要获取指向的指针`CKeyboardManager`，调用[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果你执行手动创建一个，你必须使用该方法初始化它[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。  
  
##  <a name="cleanup"></a>  CKeyboardManager::CleanUp  
 释放`CKeyboardManager`资源并清除所有快捷键密钥映射。  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>备注  
 有关键盘快捷方式的详细信息，请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。  
  
 不需要应用程序退出，因为框架将调用它自动在应用程序退出时调用此函数。  
  
##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator  
 检索指定的命令和窗口的默认快捷键。  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>参数  
 [in]*uiCmd*  
 命令 ID。  
  
 [out]*str*  
 对 `CString` 对象的引用。  
  
 [in]*pWndFrame*  
 指向框架窗口的指针。  
  
 [in]*bIsDefaultFrame*  
 指定框架窗口是否为默认框架窗口。  
  
### <a name="return-value"></a>返回值  
 如果找到该快捷方式，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法查找指定的命令通过指定*uiCmd*并检索默认快捷键。 然后该方法采用与此快捷键关联的字符串，并写入到值*str*参数。  
  
##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled  
 确定是否由处理指定的键[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)。  
  
```  
static BOOL __stdcall IsKeyHandled(
    WORD nKey,  
    BYTE fVirt,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*nKey*|要检查的键。|  
|[in]*fVirt*|指定的快捷键的行为。 有关可能的值的列表，请参阅[加速结构](http://msdn.microsoft.com/library/windows/desktop/ms646340)。|  
|[in]*pWndFrame*|框架窗口。 此方法可确定是否在此帧中处理的快捷键。|  
|[in]*bIsDefaultFrame*|一个布尔型参数，该值指示是否*pWndFrame*是默认框架窗口。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果处理的快捷键。 `FALSE` 如果密钥未被处理或如果*pWndFrame*是`NULL`。  
  
### <a name="remarks"></a>备注  
 输入的参数必须与匹配的快捷键对应表中两个条目*nKey*和*fVirt*以确定是否在中处理的快捷键*pWndFrame*。  
  
##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable  
 指示是否可打印字符。  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*nChar*|此方法检查的字符。|  
  
### <a name="return-value"></a>返回值  
 非零如果它不是，如果字符是可打印，将为零。  
  
### <a name="remarks"></a>备注  
 如果调用此方法将失败[GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299)失败。  
  
##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators  
 该值指示菜单显示所有相关联的快捷键与菜单命令或默认快捷键。  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>返回值  
 如果应用程序列出了所有快捷键的菜单命令; 则为非 0如果应用程序将显示快捷键，其默认值为 0。  
  
### <a name="remarks"></a>备注  
 应用程序列出中的菜单栏的菜单命令的快捷键。 使用函数[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)来控制是否应用程序列出所有快捷键或只是默认的快捷键。  
  
##  <a name="loadstate"></a>  CKeyboardManager::LoadState  
 从 Windows 注册表中加载的快捷键表。  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 注册表路径其中`CKeyboardManager`保存数据。  
  
 [in]*pDefaultFrame*  
 指向要用作默认窗口的框架窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果状态否则已成功加载，则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 如果*lpszProfileName*参数是`NULL`，此方法检查的默认注册表位置`CKeyboardManager`数据。 默认注册表位置由指定[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。 数据必须与方法以前编写[CKeyboardManager::SaveState](#savestate)。  
  
 如果未指定默认窗口，将使用你的应用程序的主框架窗口。  
  
##  <a name="resetall"></a>  CKeyboardManager::ResetAll  
 将重新加载的快捷键表从应用程序资源。  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>备注  
 此函数清除存储中的快捷方式`CKeyboardManager`实例。 然后，它将重新加载应用程序资源从键盘管理器的状态。  
  
##  <a name="savestate"></a>  CKeyboardManager::SaveState  
 将快捷方式表保存到 Windows 注册表中。  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszProfileName*  
 保存的注册表路径`CKeyboardManager`状态。  
  
 [in]*pDefaultFrame*  
 指向将成为默认窗口的框架窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果键盘管理器状态保存成功，则为非 0 或否则为 0。  
  
### <a name="remarks"></a>备注  
 如果*lpszProfileName*参数是`NULL`，此方法将编写`CKeyboardManager`状态到指定的默认位置[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。 如果指定的位置，则可以加载更高版本使用方法的数据[CKeyboardManager::LoadState](#loadstate)。  
  
 如果未指定默认窗口，则主框架窗口将用作默认窗口。  
  
##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators  
 显示所有相关联的快捷键与菜单命令。  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>参数  
 [in]*bShowAll*  
 如果`true`，将显示所有快捷键。 如果`false`，将显示仅第一个快捷键。  
  
 [in]*lpszDelimiter*  
 要插入之间快捷键的字符串。 如果只显示一个快捷键，则此分隔符无效。  
  
### <a name="remarks"></a>备注  
 默认情况下，如果命令具有与之关联的多个快捷键将显示仅第一个快捷键。 此函数可列出与所有命令关联的所有快捷键。  
  
 键盘快捷方式将列旁边的菜单栏中的命令。 如果所有快捷键都显示，该字符串是由*lpszDelimiter*将分隔各个快捷键。  
  
##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper  
 将字符转换为其上限的注册。  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>参数  
 [in]*nChar*  
 要转换的字符。  
  
### <a name="return-value"></a>返回值  
 上部寄存器输入参数的字符。  
  
##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable  
 使用新的快捷方式键表中更新快捷键表。  
  
```  
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    LPACCEL lpAccel,  
    int nSize,  
    CFrameWnd* pDefaultFrame = NULL);

 
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    HACCEL hAccelNew,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pTemplate*  
 文档模板指向的指针。  
  
 [in]*lpAccel*  
 指向新的快捷键的指针。  
  
 [in]*nSize*  
 新的快捷方式表的大小。  
  
 [in]*pDefaultFrame*  
 指向默认框架窗口的指针。  
  
 [in]*hAccelNew*  
 新的快捷方式表句柄。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数用于具有多个框架窗口对象的新键盘快捷键替换现有的快捷方式表。 函数会收到作为参数，以获取连接到给定的文档模板的所有框架窗口对象的访问权限的文档模板。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)



