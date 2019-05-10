---
title: DHTML 编辑命令映射
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 7f420619983283c225ca8fca23c5ea349def1d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323055"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 编辑命令映射

下列宏可用于将 DHTML 编辑命令映射[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-派生的类。 有关其用法的示例，请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="dhtml-editing-command-map-macros"></a>DHTML 编辑命令映射宏

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|声明在类中的 DHTML 编辑命令映射。|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|启动类中的 DHTML 编辑命令映射的定义。|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|将标记 DHTML 编辑命令映射的结尾。|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|将命令 ID 映射到 HTML 编辑命令。|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|将命令 ID 映射到 HTML 编辑命令和消息处理程序。|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|将命令 ID 映射到 HTML 编辑命令和用户界面元素。|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。|

##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP

声明在类中的 DHTML 编辑命令映射。

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>参数

*className*<br/>
类的名称。

### <a name="remarks"></a>备注

此宏的定义中使用，则[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-派生的类。

使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)实现映射。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP

启动类中的 DHTML 编辑命令映射的定义。

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>参数

*className*<br/>
包含 DHTML 编辑命令映射的类的名称。 此类应直接或间接派生[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)和包含[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)其类定义中的宏。

### <a name="remarks"></a>备注

将 DHTML 编辑命令映射添加到您的类将映射到 HTML 编辑命令的用户界面命令。

BEGIN_DHTMLEDITING_CMDMAP 宏放置在类的实现 (.cpp) 文件中后跟[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)类是映射 （例如，从到 IDM_CUT ID_EDIT_CUT) 的命令的宏。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)宏来标记事件映射的结尾。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP

将标记 DHTML 编辑命令映射的结尾。

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>备注

结合使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY

将命令 ID 映射到 HTML 编辑命令。

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID （例如 ID_EDIT_COPY) 中。

*dhtmlcmdID*<br/>
HTML 编辑命令所属*cmdID*映射 （例如 2&gt;idm_copy&lt;2)。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC

将命令 ID 映射到 HTML 编辑命令和消息处理程序。

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID （例如 ID_EDIT_COPY) 中。

*dhtmlcmdID*<br/>
HTML 编辑命令所属*cmdID*映射 （例如 2&gt;idm_copy&lt;2)。

*member_func_name*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE

将命令 ID 映射到 HTML 编辑命令和用户界面元素。

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID （例如 ID_EDIT_COPY) 中。

*dhtmlcmdID*<br/>
HTML 编辑命令所属*cmdID*映射 （例如 2&gt;idm_copy&lt;2)。

*elemType*<br/>
用户界面元素类型;AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 之一。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID （例如 ID_EDIT_COPY) 中。

*dhtmlcmdID*<br/>
HTML 编辑命令所属*cmdID*映射 （例如 2&gt;idm_copy&lt;2)。

*member_func_name*<br/>
命令映射到的消息处理程序函数的名称。

*elemType*<br/>
用户界面元素类型;AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 之一。

### <a name="example"></a>示例

请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **标头**afxhtml.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
