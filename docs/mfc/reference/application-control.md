---
title: 应用程序控制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 538a376dd14eae32864b494b7e79db1c89686b84
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315010"
---
# <a name="application-control"></a>应用程序控件
OLE 需要大量控制应用程序和它们的对象。 OLE 系统 Dll 必须能够启动和自动发布的应用程序、 协调他们的生产和修改对象，等等。 本主题中的函数符合这些要求。 有时必须调用由 OLE 系统 Dll，除了通过应用程序以及上调用这些函数。 
  
### <a name="application-control"></a>应用程序控件  
  
|||  
|-|-|  
|[AfxOleCanExitApp](#afxolecanexitapp)|指示应用程序是否可以终止。|  
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|检索应用程序的当前消息筛选器。|  
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|检索当前用户控件标志。|  
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|设置或清除用户控件标志。|  
|[AfxOleLockApp](#afxolelockapp)|增加应用程序中的活动对象数的框架的全局的计数。|  
|[AfxOleLockControl](#afxolelockcontrol)| 锁定指定控件的类工厂。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|递减框架的应用程序中的活动对象数的计数。| 
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 解除锁定指定控件的类工厂。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|OLE 系统注册表中注册服务器。|  
|[AfxOleSetEditMenu](#afxoleseteditmenu)|实现的用户界面*typename*对象命令。|  

  
##  <a name="afxolecanexitapp"></a>  AfxOleCanExitApp  
 指示应用程序是否可以终止。  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>返回值  
 如果应用程序退出，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在对应用程序的对象的未处理引用，则应用程序不应终止。 全局函数 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分别对应用程序对象引用计数器进行递增和递减。 当此计数器为非零时，应用程序不应终止。 如果计数器为非零，当用户从系统菜单选择“关闭”或从“文件”菜单选择“退出”时，应用程序的主窗口将会隐藏（不销毁）。 框架调用此函数`CFrameWnd::OnClose`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>要求  
 **标头**: afxdisp.h 

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter  
 检索应用程序的当前消息筛选器。  
  
```   
COleMessageFilter* AFXAPI AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>返回值  
 指向当前消息筛选器的指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可访问当前 `COleMessageFilter` 派生的对象，这与调用 `AfxGetApp` 来访问当前应用程序对象一样。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>要求  
 **标头**: afxwin.h 

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl  
 检索当前用户控件标志。  
  
```   
BOOL AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>返回值  
 如果用户位于应用程序控件内，则不为零；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果用户已显式打开或创建新文档，则用户将位于应用程序控件内。 如果应用程序不是由 OLE 系统 DLL 启动的 - 换句话说，如果用户使用系统 Shell 启动了应用程序，则用户也将位于控件内。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl  
 设置或清除用户控件标志，参考 》 中所述`AfxOleGetUserCtrl`。  
  
```  
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>参数  
 *bUserCtrl*  
 指定是否要设置或清除该用户控件标志。  
  
### <a name="remarks"></a>备注  
 框架调用此函数时在用户创建或加载一个文档，但不是加载或间接操作时，例如从容器应用程序加载嵌入的对象通过创建文档时。  
  
 如果你的应用程序中的其他操作应将用户放在应用程序的控制，请调用此函数。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp  
 增加应用程序中的活动对象数的框架的全局的计数。  
  
```   
void AFXAPI AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>备注  
 框架保留应用程序中处于活动状态的对象数的计数。 `AfxOleLockApp`和`AfxOleUnlockApp`函数分别，递增和递减此计数。  
  
 当用户尝试关闭的应用程序的活动对象 — 其活动对象计数为非零值的应用程序 — framework 会隐藏从用户的视图，而不是完全关闭该应用程序。 `AfxOleCanExitApp`函数指示是否可以终止该应用程序。  
  
 调用`AfxOleLockApp`从公开 OLE 接口，如果客户端应用程序仍在使用时销毁该对象不需要任何对象。 此外调用`AfxOleUnlockApp`的任何对象，以调用析构函数中`AfxOleLockApp`构造函数中。 默认情况下， `COleDocument` （和派生类） 会自动锁定和解锁应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp  
 递减框架的应用程序中的活动对象计数。  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>备注  
 请参阅`AfxOleLockApp`有关进一步信息。  
  
 当活动对象数达到零时，`AfxOleOnReleaseAllObjects`调用。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[AfxOleLockApp](#afxolelockapp)。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h  

 ## <a name="afxolelockcontrol"></a>AfxOleLockControl
锁定指定控件的类工厂，以便与此控件关联的动态创建的数据保留在内存中。  
   
### <a name="syntax"></a>语法    
```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );  
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>参数  
 *clsid*  
 控件的唯一类 ID。  
  
 *lpszProgID*  
 控件的唯一程序 ID。  
   
### <a name="return-value"></a>返回值  
 如果控件的类工厂成功锁定，则不为零；否则为 0。  
   
### <a name="remarks"></a>备注  
 这可以明显加速控件的显示。 例如，一旦在对话框中创建控件并使用 `AfxOleLockControl` 锁定控件，则无需在每次显示或销毁对话框时创建和删除它。 如果用户反复打开并关闭对话框，则锁定控件可以显著提高性能。 准备销毁控件时，请调用 `AfxOleUnlockControl`。  
   
### <a name="example"></a>示例  
```cpp
// Starts and locks control's (Microsoft Calendar) class factory. 
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```
   
### <a name="requirements"></a>要求  
 **标头:** afxwin.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxOleUnlockControl](#afxoleunlockcontrol)
 
##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass  
 此函数，可在 OLE 系统注册表中注册你的服务器。  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>参数  
 *clsid*  
 对服务器的 OLE 类 id。  
  
 *lpszClassName*  
 包含服务器的对象的类名称的字符串指针。  
  
 *lpszShortTypeName*  
 包含服务器的对象类型，如"图。"的短名称的字符串指针  
  
 *lpszLongTypeName*  
 包含服务器的对象类型，如"Microsoft Excel 5.0 图。"的长名称的字符串指针  
  
 *nAppType*  
 一个值，从 OLE_APPTYPE 枚举，指定的 OLE 应用程序的类型。 可能的值如下所示：  
  
- OAT_INPLACE_SERVER 服务器具有完全服务器用户界面。  
  
- OAT_SERVER 服务器支持只嵌入。  
  
- OAT_CONTAINER 容器支持链接到嵌入。  
  
- OAT_DISPATCH_OBJECT `IDispatch`-支持的对象。  
  
 *rglpszRegister*  
 指向字符串表示的键和值添加到 OLE 系统注册表，如果找不到键的任何现有值的指针的数组。  
  
 *rglpszOverwrite*  
 指向字符串表示的键和值添加到 OLE 系统注册表，如果注册表包含给定键的现有值的指针的数组。  
  
### <a name="return-value"></a>返回值  
 如果成功注册服务器类; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 大多数应用程序可以使用`COleTemplateServer::Register`注册应用程序的文档类型。 如果应用程序的系统注册表格式不适合的典型模式，则可以使用`AfxOleRegisterServerClass`更多控制。  
  
 注册表包含键和值的一组。 *RglpszRegister*并*rglpszOverwrite*参数是指向字符串的指针的数组，其中每个包括的一个键和值分隔**NULL**字符 ( `'\0'`). 每个这些字符串可以其位置被标记为字符序列的可替换参数 *%1*通过 *%5*。  
  
 按如下所示填充符号：  
  
|符号|“值”|  
|------------|-----------|  
|%1|类 ID，格式为字符串|  
|%2|类名|  
|%3|可执行文件路径|  
|%4|短类型名称|  
|%5|Long 类型名称|  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu  
 实现的用户界面*typename*对象命令。  
  
```   
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>参数  
 *pClient*  
 指向客户端 OLE 项的指针。  
  
 *pMenu*  
 指向要更新的菜单对象的指针。  
  
 *iMenuItem*  
 要更新的菜单项的索引。  
  
 *nIDVerbMin*  
 对应于主谓词命令 ID。  
  
 *nIDVerbMax*  
 对应于上次谓词命令 ID。  
  
 *nIDConvert*  
 转换菜单项的 ID。  
  
### <a name="remarks"></a>备注  
 如果服务器认识到主谓词，菜单项将成为"谓词*typename*对象"和*nIDVerbMin*当用户选择该命令发送命令。 如果服务器认识到多个谓词，则菜单项将成为" *typename*对象"，并列出所有谓词的子菜单显示在用户选择该命令时。 当用户从子菜单中，选择一个动词*nIDVerbMin*如果选择第一个谓词，则发送*nIDVerbMin* + 1 发送如果第二个谓词为所选，等等。 默认值`COleDocument`实现自动处理此功能。  
  
 下面的语句必须在客户端的应用程序资源脚本 (。RC) 文件：  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>要求  
 **标头**: afxole.h 

## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl
解除锁定指定控件的类工厂。  
   
### <a name="syntax"></a>语法  
```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );  
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>参数  
 *clsid*  
 控件的唯一类 ID。  
  
 *lpszProgID*  
 控件的唯一程序 ID。  
   
### <a name="return-value"></a>返回值  
 如果该控件的类工厂成功锁定，则非零值否则为 0。  
   
### <a name="remarks"></a>备注  
 使用锁定控件`AfxOleLockControl`，以便动态地创建与控件关联的数据保留在内存中。 这可以显著加快控件显示因为该控件不需要创建和销毁每次它会显示。 准备销毁控件时，请调用 `AfxOleUnlockControl`。  
   
### <a name="example"></a>示例  
```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```
   
### <a name="requirements"></a>要求  
 **标头:** afxwin.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)  
 [AfxOleLockControl](#afxolelockcontrol)

