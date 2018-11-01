---
title: DELETEITEMSTRUCT 结构
ms.date: 11/04/2016
f1_keywords:
- DELETEITEMSTRUCT
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
ms.openlocfilehash: dd1f48fd584016dab740bc8a6bd05ff3b756e41b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486874"
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT 结构

`DELETEITEMSTRUCT` 结构介绍了一个已删除的所有者描述的列表框或组合框项。

## <a name="syntax"></a>语法

```
typedef struct tagDELETEITEMSTRUCT { /* ditms */
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    HWND hwndItem;
    UINT itemData;
} DELETEITEMSTRUCT;
```

#### <a name="parameters"></a>参数

*CtlType*<br/>
指定 ODT_LISTBOX （一个所有者描述的列表框） 或 ODT_COMBOBOX （一个所有者描述的组合框）。

*CtlID*<br/>
指定列表框或组合框的标识符。

*itemID*<br/>
指定要移除的列表框或组合框中的项的索引。

*hwndItem*<br/>
标识控件。

*itemData*<br/>
为该项指定应用程序定义的数据。 此值传递到中的控件*lParam*将项添加到列表框或组合框的消息参数。

## <a name="remarks"></a>备注

从列表框或组合框或销毁列表框或组合框删除某个项后，Windows 将 WM_DELETEITEM 消息发送到每个已删除的项的所有者。 *LParam*消息参数包含指向此结构的指针。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)

