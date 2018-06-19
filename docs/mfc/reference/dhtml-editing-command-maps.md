---
title: DHTML 编辑命令映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69630d00b09534d97d5e46a8400b73f0e9d85b24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375130"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 编辑命令映射
可以使用以下宏映射 DHTML 编辑命令[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-派生类。 有关其使用的示例，请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="dhtml-editing-command-map-macros"></a>DHTML 编辑命令映射宏  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|声明 DHTML 编辑命令映射类中。|  
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|启动 DHTML 编辑命令映射类内部的定义。|  
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|标记 DHTML 编辑命令映射的末尾。|  
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|命令 ID 映射到 HTML 编辑命令。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|命令 ID 映射到 HTML 编辑命令和消息处理程序。|  
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|命令 ID 映射到 HTML 编辑命令和用户界面元素。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP  
 声明 DHTML 编辑命令映射类中。  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 类的名称。  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-派生类。  
  
 使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)实现映射。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP  
 启动 DHTML 编辑命令映射类内部的定义。  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 编辑命令映射的类名称。 此类应直接或间接派生从[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)和包括[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 编辑命令映射添加到你的类以将用户界面命令映射到 HTML 编辑命令。  
  
 位置`BEGIN_DHTMLEDITING_CMDMAP`类的实现 (.cpp) 文件中的宏跟[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)用于此类是映射的命令的宏 (例如，从**ID_EDIT_CUT**到**IDM_CUT**)。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)宏来标记事件映射的末尾。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP  
 标记 DHTML 编辑命令映射的末尾。  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>备注  
 结合使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY  
 命令 ID 映射到 HTML 编辑命令。  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 命令 ID (如**ID_EDIT_COPY**)。  
  
 `dhtmlcmdID`  
 HTML 编辑命令向其`cmdID`映射 (如**IDM_COPY**)。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC  
 命令 ID 映射到 HTML 编辑命令和消息处理程序。  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 命令 ID (如**ID_EDIT_COPY**)。  
  
 `dhtmlcmdID`  
 HTML 编辑命令向其`cmdID`映射 (如**IDM_COPY**)。  
  
 `member_func_name`  
 命令映射到的消息处理程序函数的名称。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE  
 命令 ID 映射到 HTML 编辑命令和用户界面元素。  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 命令 ID (如**ID_EDIT_COPY**)。  
  
 `dhtmlcmdID`  
 HTML 编辑命令向其`cmdID`映射 (如**IDM_COPY**)。  
  
 `elemType`  
 用户界面元素类型;之一**AFX_UI_ELEMTYPE_NORMAL**， **AFX_UI_ELEMTYPE_CHECKBOX**，或**AFX_UI_ELEMTYPE_RADIO**。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE  
 将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 命令 ID (如**ID_EDIT_COPY**)。  
  
 `dhtmlcmdID`  
 HTML 编辑命令向其`cmdID`映射 (如**IDM_COPY**)。  
  
 `member_func_name`  
 命令映射到的消息处理程序函数的名称。  
  
 `elemType`  
 用户界面元素类型;之一**AFX_UI_ELEMTYPE_NORMAL**， **AFX_UI_ELEMTYPE_CHECKBOX**，或**AFX_UI_ELEMTYPE_RADIO**。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  

### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
