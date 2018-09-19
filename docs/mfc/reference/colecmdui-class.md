---
title: COleCmdUI 类 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ece2d45bdce490d09c7195deec380728d79392d
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535220"
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
  
|名称|描述|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|设置或清除启用命令标志。|  
|[COleCmdUI::SetCheck](#setcheck)|设置打开/关闭切换状态命令。|  
|[COleCmdUI::SetText](#settext)|返回命令的文本名称或状态字符串。|  
  
## <a name="remarks"></a>备注  
 应用程序中，未启用为 DocObjects，当一个应用程序，MFC 菜单中的用户视图处理 UPDATE_COMMAND_UI 通知。 提供每个通知[CCmdUI](../../mfc/reference/ccmdui-class.md)可以操作以反映特定命令的状态的对象。 但是，当 DocObjects 启用了你的应用程序，则 MFC 将处理 UPDATE_OLE_COMMAND_UI 通知，将分配`COleCmdUI`对象。  
  
 `COleCmdUI` 允许 DocObject 为接收源自其容器的用户界面 （如 filenew、 打开、 打印和等等） 中的命令，并允许容器接收源自该文档的用户界面中的命令。 尽管`IDispatch`无法用于调度相同的命令，`IOleCommandTarget`提供更简单的方法来查询和执行，因为它依赖于一组标准的命令，通常不使用参数，且涉及无类型信息。 `COleCmdUI` 可用于启用、 更新和设置其他属性 DocObject 用户界面命令。 当你想要调用的命令时，调用[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。  
  
 DocObjects 的详细信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)并[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdocobj.h  
  
##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI  
 构造`COleCmdUI`与特定的用户界面命令相关联的对象。  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>参数  
 *rgCmds*  
 与给定 GUID 关联的受支持命令的列表。 `OLECMD`结构将命令与命令标志相关联。  
  
 *cCmds*  
 中的命令计数*rgCmds*。  
  
 *pGroup*  
 指向标识一系列命令的 GUID 的指针。  
  
### <a name="remarks"></a>备注  
 `COleCmdUI`对象提供一种编程接口的更新 DocObject 如菜单项或控件条按钮的用户界面对象。 可以启用、 禁用、 清除通过用户界面对象和选中状态，`COleCmdUI`对象。  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 调用此函数可设置的命令标志`COleCmdUI`对象到 OLECOMDF_ENABLED，它指示该命令，并启用该接口，或清除命令标志。  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>参数  
 *bOn*  
 指示是否使用关联的命令`COleCmdUI`对象应启用或禁用。 Nonzero 启用命令;0 会禁用此命令。  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 调用此函数可设置的状态的打开/关闭切换命令。  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>参数  
 *n 请查看*  
 一个值用于确定要设置打开/关闭切换的状态命令。 值为：  
  
|“值”|描述|  
|-----------|-----------------|  
|**1**|将该命令设置为 on。|  
|**2**|将该命令设置为不确定的;无法确定状态，因为此命令的属性是在同时打开和关闭相关的所选内容中的状态。|  
|任何其他值|设置为 off 的命令。|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 调用此函数可返回命令的文本名称或状态字符串。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 指向要与命令一起使用的文本的指针。  
  
## <a name="see-also"></a>请参阅  
 [CCmdUI 类](../../mfc/reference/ccmdui-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



