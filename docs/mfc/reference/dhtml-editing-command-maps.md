---
title: "DHTML 编辑命令映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
caps.latest.revision: 14
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
ms.openlocfilehash: 89aa66d3a1e85183baaba21f001b60e080895f7f
ms.lasthandoff: 02/24/2017

---
# <a name="dhtml-editing-command-maps"></a>DHTML 编辑命令映射
下列宏可用于将 DHTML 编辑命令映射[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)的派生类。 有关其用法的示例，请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="dhtml-editing-command-map-macros"></a>DHTML 编辑命令映射宏  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|声明类中的 DHTML 编辑命令映射。|  
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|启动 DHTML 编辑命令映射类中的定义。|  
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|将标记 DHTML 编辑命令映射的结尾。|  
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|将命令 ID 映射到 HTML 编辑命令。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|将命令 ID 映射到 HTML 编辑命令和消息处理程序。|  
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|将命令 ID 映射到 HTML 编辑命令和用户界面元素。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。|  
  
##  <a name="a-namedeclaredhtmleditingcmdmapa--declaredhtmleditingcmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP  
 声明类中的 DHTML 编辑命令映射。  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 类的名称。  
  
### <a name="remarks"></a>备注  
 此宏的定义中使用，则[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)的派生类。  
  
 使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)来实现该映射。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="a-namebegindhtmleditingcmdmapa--begindhtmleditingcmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP  
 启动 DHTML 编辑命令映射类中的定义。  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>参数  
 `className`  
 包含 DHTML 编辑命令映射的类的名称。 此类应直接或间接派生从[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)并且包括[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)在其类定义中的宏。  
  
### <a name="remarks"></a>备注  
 将 DHTML 编辑命令映射添加到您的类将映射到 HTML 编辑命令的用户界面命令。  
  
 位置`BEGIN_DHTMLEDITING_CMDMAP`类的实现 (.cpp) 文件中的宏跟[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)宏的类是映射的命令 (例如，从**ID_EDIT_CUT**到**IDM_CUT**)。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)宏来标记事件映射的末尾。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="a-nameenddhtmleditingcmdmapa--enddhtmleditingcmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP  
 将标记 DHTML 编辑命令映射的结尾。  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>备注  
 结合使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="a-namedhtmleditingcmdentrya--dhtmleditingcmdentry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY  
 将命令 ID 映射到 HTML 编辑命令。  
  
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
  
##  <a name="a-namedhtmleditingcmdentryfunca--dhtmleditingcmdentryfunc"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC  
 将命令 ID 映射到 HTML 编辑命令和消息处理程序。  
  
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
  
##  <a name="a-namedhtmleditingcmdentrytypea--dhtmleditingcmdentrytype"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE  
 将命令 ID 映射到 HTML 编辑命令和用户界面元素。  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>参数  
 `cmdID`  
 命令 ID (如**ID_EDIT_COPY**)。  
  
 `dhtmlcmdID`  
 HTML 编辑命令向其`cmdID`映射 (如**IDM_COPY**)。  
  
 `elemType`  
 用户界面元素类型;其中一个**AFX_UI_ELEMTYPE_NORMAL**， **AFX_UI_ELEMTYPE_CHECKBOX**，或**AFX_UI_ELEMTYPE_RADIO**。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
  
##  <a name="a-namedhtmleditingcmdentryfunctypea--dhtmleditingcmdentryfunctype"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE  
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
 用户界面元素类型;其中一个**AFX_UI_ELEMTYPE_NORMAL**， **AFX_UI_ELEMTYPE_CHECKBOX**，或**AFX_UI_ELEMTYPE_RADIO**。  
  
### <a name="example"></a>示例  
 请参阅[HTMLEdit 示例](../../visual-cpp-samples.md)。  

### <a name="requirements"></a>要求  
  **标头**afxhtml.h  
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

