---
title: COleDialog 类
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366093"
---
# <a name="coledialog-class"></a>COleDialog 类

提供 OLE 对话框共有的功能。

## <a name="syntax"></a>语法

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDialog：获取最后错误](#getlasterror)|获取对话框返回的错误代码。|

## <a name="remarks"></a>备注

Microsoft 基础类库提供来自`COleDialog`的多个类：

- [COleInsert对话](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIcon对话](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusy对话](../../mfc/reference/colebusydialog-class.md)

- [COle 更新对话](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COle属性对话](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

有关特定于 OLE 的对话框的详细信息，请参阅 OLE[中的"对话框](../../mfc/dialog-boxes-in-ole.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>要求

**标题：** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog：获取最后错误

调用`GetLastError`成员函数以在返回 IDABORT`DoModal`时获取其他错误信息。

```
UINT GetLastError() const;
```

### <a name="return-value"></a>返回值

返回`GetLastError`的错误代码取决于显示的特定对话框。

### <a name="remarks"></a>备注

有关特定`DoModal`错误消息的信息，请参阅派生类中的成员函数。

## <a name="see-also"></a>另请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
