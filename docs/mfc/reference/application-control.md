---
title: "应用程序控制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 81eb0bcdd8c9d154f62635e7f306cefcf7a15c1b
ms.lasthandoff: 02/24/2017

---
# <a name="application-control"></a>应用程序控件
OLE 要求大量地控制应用程序和它们的对象。 OLE 系统 Dll 必须能够启动并自动发布的应用程序、 协调他们的生产和修改的对象，依次类推。 本主题中的函数满足这些要求。 有时必须调用由 OLE 系统 Dll，除了通过应用程序以及上调用这些函数。  
  
### <a name="application-control"></a>应用程序控件  
  
|||  
|-|-|  
|[AfxOleCanExitApp](#afxolecanexitapp)|指示应用程序是否可以终止。|  
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|检索应用程序的当前消息筛选器。|  
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|检索当前用户控件标志。|  
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|设置或清除用户控件标志。|  
|[AfxOleLockApp](#afxolelockapp)|递增应用程序中的活动对象数的框架的全局的计数。|  
|[AfxOleUnlockApp](#afxoleunlockapp)|递减的应用程序中的活动对象数的框架的计数。|  
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|OLE 系统注册表中注册服务器。|  
|[AfxOleSetEditMenu](#afxoleseteditmenu)|实现的用户界面*typename*对象命令。|  
  
##  <a name="a-nameafxolecanexitappa--afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp  
 指示应用程序是否可以终止。  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>返回值  
 如果应用程序退出，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果存在对应用程序的对象的未处理引用，则应用程序不应终止。 全局函数 `AfxOleLockApp` 和 `AfxOleUnlockApp` 分别对应用程序对象引用计数器进行递增和递减。 当此计数器为非零时，应用程序不应终止。 如果计数器为非零，当用户从系统菜单选择“关闭”或从“文件”菜单选择“退出”时，应用程序的主窗口将会隐藏（不销毁）。 框架将调用此函数**cframewnd:: Onclose**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation #&2;](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>要求  
 **标头**: afxdisp.h 

##  <a name="a-nameafxolegetmessagefiltera--afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter  
 检索应用程序的当前消息筛选器。  
  
```   
COleMessageFilter* AFXAPI  AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>返回值  
 指向当前消息筛选器的指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可访问当前 `COleMessageFilter` 派生的对象，这与调用 `AfxGetApp` 来访问当前应用程序对象一样。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation #&3;](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation #&4;](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>要求  
 **标头**: afxwin.h 

##  <a name="a-nameafxolegetuserctrla--afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl  
 检索当前用户控件标志。  
  
```   
BOOL  AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>返回值  
 如果用户位于应用程序控件内，则不为零；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果用户已显式打开或创建新文档，则用户将位于应用程序控件内。 如果应用程序不是由 OLE 系统 DLL 启动的 - 换句话说，如果用户使用系统 Shell 启动了应用程序，则用户也将位于控件内。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="a-nameafxolesetuserctrla--afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl  
 设置或清除用户控件标志，参考 》 中所述`AfxOleGetUserCtrl`。  
  
```  
void  AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>参数  
 *bUserCtrl*  
 指定是否要设置或清除用户控件标志。  
  
### <a name="remarks"></a>备注  
 框架调用此函数时在用户创建或加载文档，但不是在加载或通过的间接操作，例如从容器应用程序加载嵌入的对象创建一个文档。  
  
 如果您的应用程序中的其他操作应将用户放在应用程序的控制，请调用此函数。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="a-nameafxolelockappa--afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp  
 递增应用程序中的活动对象数的框架的全局的计数。  
  
```   
void  AFXAPI  AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>备注  
 框架保留应用程序中处于活动状态的对象数的计数。 `AfxOleLockApp`和`AfxOleUnlockApp`函数分别递增和递减此计数。  
  
 当用户尝试关闭具有活动的对象的应用程序 — 应用程序的活动对象计数为非零值 — framework 隐藏从用户的视图，而不是完全关闭该应用程序。 `AfxOleCanExitApp`函数指示是否可以终止该应用程序。  
  
 调用`AfxOleLockApp`从公开 OLE 接口，如果不希望出现在客户端应用程序仍在使用时销毁该对象的任何对象。 此外调用`AfxOleUnlockApp`调用任何对象的析构函数中`AfxOleLockApp`构造函数中。 默认情况下， `COleDocument` （和派生类） 会自动锁定和解锁应用程序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation #&5;](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="a-nameafxoleunlockappa--afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp  
 递减框架的应用程序中的活动对象计数。  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>备注  
 请参阅`AfxOleLockApp`有关详细信息。  
  
 当活动对象的数目为零时， **AfxOleOnReleaseAllObjects**调用。  
  
### <a name="example"></a>示例  
 请参阅示例[AfxOleLockApp](#afxolelockapp)。  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h  

##  <a name="a-nameafxoleregisterserverclassa--afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass  
 此函数允许您在 OLE 系统注册表中注册您的服务器。  
  
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
 `clsid`  
 引用服务器的 OLE 类 id。  
  
 `lpszClassName`  
 包含服务器的对象的类名的字符串的指针。  
  
 *lpszShortTypeName*  
 包含服务器的对象类型，如"图。"的短名称的字符串的指针  
  
 *lpszLongTypeName*  
 包含服务器的对象类型，如"Microsoft Excel 5.0 图表。"的长名称的字符串的指针  
  
 `nAppType`  
 一个值，取自**OLE_APPTYPE**指定 OLE 应用程序的类型的枚举。 可能的值如下所示︰  
  
- `OAT_INPLACE_SERVER`服务器有完整服务器用户界面。  
  
- `OAT_SERVER`服务器支持只嵌入。  
  
- `OAT_CONTAINER`容器支持链接到嵌入。  
  
- `OAT_DISPATCH_OBJECT``IDispatch`-支持的对象。  
  
 `rglpszRegister`  
 表示的键和值添加到 OLE 系统注册表中，如果找不到键的任何现有值的以字符串的指针的数组。  
  
 `rglpszOverwrite`  
 表示的键和值添加到 OLE 系统注册表中，如果注册表包含给定的键的现有值的以字符串的指针的数组。  
  
### <a name="return-value"></a>返回值  
 如果成功注册服务器类则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 大多数应用程序可以使用**COleTemplateServer::Register**注册应用程序的文档类型。 如果应用程序的系统注册表格式不适合的典型模式，则可以使用`AfxOleRegisterServerClass`获得更多控制。  
  
 注册表包含键和值的组。 `rglpszRegister`和`rglpszOverwrite`参数是指向字符串的指针的数组，其中每个包括的一个键和值之间用**NULL**字符 ( `'\0'`)。 其中每个字符串可以有其位置的字符序列被标记为可替换参数`%1`通过`%5`。  
  
 符号填充了如下︰  
  
|符号|值|  
|------------|-----------|  
|%1|类 ID，格式为字符串|  
|%2|类名|  
|%3|可执行文件路径|  
|%4|短类型名称|  
|%5|Long 类型名称|  

### <a name="requirements"></a>要求  
 **标头**: afxdisp.h

##  <a name="a-nameafxoleseteditmenua--afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu  
 实现的用户界面*typename*对象命令。  
  
```   
void  AFXAPI  AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>参数  
 `pClient`  
 客户端 OLE 项的指针。  
  
 `pMenu`  
 指向要更新菜单对象的指针。  
  
 *iMenuItem*  
 要更新的菜单项的索引。  
  
 `nIDVerbMin`  
 对应于主谓词的命令 ID。  
  
 *nIDVerbMax*  
 对应于上次谓词的命令 ID。  
  
 *nIDConvert*  
 Convert 菜单项的 ID。  
  
### <a name="remarks"></a>备注  
 如果服务器能够识别主谓词，菜单项将成为"谓词*typename*对象"和`nIDVerbMin`发送命令时，当用户选择该命令。 如果服务器能够识别多个谓词，则该菜单项将成为" *typename*对象"，并列出所有谓词的子菜单显示在用户选择该命令时。 当用户从子菜单中，选择一个动词`nIDVerbMin`如果选择第一个谓词，则发送`nIDVerbMin`+ 1 发送如果第二项操作是选，等等。 默认值`COleDocument`实现自动处理此功能。  
  
 下面的语句必须在您的客户端应用程序资源脚本 (。RC) 文件︰  
  
 **#include \<afxolecl.rc&1;>**  

### <a name="requirements"></a>要求  
 **标头**: afxole.h 

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

