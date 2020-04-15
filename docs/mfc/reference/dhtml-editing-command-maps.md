---
title: DHTML 编辑命令映射
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365823"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 编辑命令映射

以下宏可用于映射[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)派生类中的 DHTML 编辑命令。 有关它们的使用示例，请参阅[HTMLEdit 示例](../../overview/visual-cpp-samples.md)。

### <a name="dhtml-editing-command-map-macros"></a>DHTML 编辑命令映射宏

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|在类中声明 DHTML 编辑命令映射。|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|在类中启动 DHTML 编辑命令映射的定义。|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|标记 DHTML 编辑命令映射的末尾。|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|将命令 ID 映射到 HTML 编辑命令。|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|将命令 ID 映射到 HTML 编辑命令和消息处理程序。|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|将命令 ID 映射到 HTML 编辑命令和用户界面元素。|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

在类中声明 DHTML 编辑命令映射。

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
类的名称。

### <a name="remarks"></a>备注

此宏将用于[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)派生类的定义。

使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)实现映射。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

在类中启动 DHTML 编辑命令映射的定义。

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>参数

*类名称*<br/>
包含 DHTML 编辑命令映射的类的名称。 此类应直接或间接地派生自[CHtmlEditView，](../../mfc/reference/chtmleditview-class.md)并在其类定义中包括[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)宏。

### <a name="remarks"></a>备注

向类添加 DHTML 编辑命令映射，将用户界面命令映射到 HTML 编辑命令。

将BEGIN_DHTMLEDITING_CMDMAP宏放在类的实现 （.cpp）[文件中，然后](#dhtmlediting_cmd_entry)DHTMLEDITING_CMD_ENTRY宏，用于类要映射的命令（例如，从ID_EDIT_CUT到IDM_CUT）。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)宏标记事件映射的结尾。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

标记 DHTML 编辑命令映射的末尾。

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>备注

与[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)一起使用。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

将命令 ID 映射到 HTML 编辑命令。

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID（如 ID_EDIT_COPY）。

*dhtmlcmdID*<br/>
CMdID 映射到哪个*cmdID*的 HTML 编辑命令（如IDM_COPY）。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

将命令 ID 映射到 HTML 编辑命令和消息处理程序。

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID（如 ID_EDIT_COPY）。

*dhtmlcmdID*<br/>
CMdID 映射到哪个*cmdID*的 HTML 编辑命令（如IDM_COPY）。

*member_func_name*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

将命令 ID 映射到 HTML 编辑命令和用户界面元素。

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID（如 ID_EDIT_COPY）。

*dhtmlcmdID*<br/>
CMdID 映射到哪个*cmdID*的 HTML 编辑命令（如IDM_COPY）。

*埃莱姆类型*<br/>
用户界面元素类型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 之一。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

将命令 ID 映射到 HTML 编辑命令、消息处理程序和用户界面元素。

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>参数

*cmdID*<br/>
命令 ID（如 ID_EDIT_COPY）。

*dhtmlcmdID*<br/>
CMdID 映射到哪个*cmdID*的 HTML 编辑命令（如IDM_COPY）。

*member_func_name*<br/>
命令映射到的消息处理程序函数的名称。

*埃莱姆类型*<br/>
用户界面元素类型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 之一。

### <a name="example"></a>示例

请参阅[HTML 编辑示例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>要求

  **头**afxhtml.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
