---
title: "COleCmdUI 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleCmdUI
dev_langs:
- C++
helpviewer_keywords:
- document object server
- COleCmdUI class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 38e7019d7636166262028d955455cee675824f8b
ms.lasthandoff: 02/24/2017

---
# <a name="colecmdui-class"></a>COleCmdUI 类
实现 MFC 方法以更新与应用程序的 `IOleCommandTarget`驱动功能相关的用户界面对象的状态。  
  
## <a name="syntax"></a>语法  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|构造 `COleCmdUI` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|设置或清除启用命令标志。|  
|[COleCmdUI::SetCheck](#setcheck)|设置的状态打开/关闭切换命令。|  
|[COleCmdUI::SetText](#settext)|返回命令的文本名称或状态字符串。|  
  
## <a name="remarks"></a>备注  
 没有为启用 DocObjects，当用户在应用程序，MFC 进程中查看一个菜单，应用程序中**UPDATE_COMMAND_UI**通知。 每个通知被授权者提供[CCmdUI](../../mfc/reference/ccmdui-class.md)可以对其进行操作，以反映特定命令的状态的对象。 但是，当为 DocObjects 启用您的应用程序，则 MFC 将处理**UPDATE_OLE_COMMAND_UI**通知，并将分配`COleCmdUI`对象。  
  
 `COleCmdUI`允许 DocObject 能够接收命令源自其容器的用户界面 （如 FileNew、 打开、 打印等），并允许容器接收源自 DocObject 的用户界面的命令。 尽管`IDispatch`无法用于调度相同的命令，`IOleCommandTarget`提供了一种更简单的方法来查询和执行，因为它依赖于一组标准的命令，通常不使用参数，并且不涉及任何类型信息。 `COleCmdUI`可用于启用、 更新和设置其他属性 DocObject 用户界面命令。 当您想要调用的命令时，调用[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。  
  
 DocObjects 的进一步信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。 另请参阅[Internet 前几个步骤︰ 活动文档](../../mfc/active-documents-on-the-internet.md)和[活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdocobj.h  
  
##  <a name="a-namecolecmduia--colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI  
 构造`COleCmdUI`与特定的用户界面命令相关联的对象。  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>参数  
 `rgCmds`  
 与给定 GUID 相关联的受支持命令的列表。 **OLECMD**命令标志与结构相关联的命令。  
  
 *cCmds*  
 中的命令计数`rgCmds`。  
  
 `pGroup`  
 一个指向一个 GUID，标识一组命令。  
  
### <a name="remarks"></a>备注  
 `COleCmdUI`对象提供用于更新菜单项或控件条按钮之类的 DocObject 用户界面对象的编程接口。 可以启用、 禁用、 清除通过用户界面对象和选中状态，`COleCmdUI`对象。  
  
##  <a name="a-nameenablea--colecmduienable"></a><a name="enable"></a>COleCmdUI::Enable  
 调用此函数可设置的命令标志`COleCmdUI`对象传递给**OLECOMDF_ENABLED**，该参数告诉界面命令是否可用，且已启用，或清除的命令标志。  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>参数  
 `bOn`  
 指示该命令与`COleCmdUI`对象应启用还是禁用。 Nonzero 使命令;0 禁用的命令。  
  
##  <a name="a-namesetchecka--colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck  
 调用此函数可设置的状态的开/关切换命令。  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>参数  
 `nCheck`  
 值，用于确定要设置开/关切换的状态命令。 值为：  
  
|值|说明|  
|-----------|-----------------|  
|**1**|将该命令设置为 on。|  
|**2**|将该命令设置为不确定的;因为此命令的属性是在同时打开和关闭相关的所选内容中的状态不确定状态。|  
|任何其他值|设置为 off 的命令。|  
  
##  <a name="a-namesettexta--colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText  
 调用此函数可返回命令的文本名称或状态字符串。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指向要与命令一起使用的文本指针。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdUI 类](../../mfc/reference/ccmdui-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




