---
title: 类型库访问
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372878"
---
# <a name="type-library-access"></a>类型库访问

类型库向其他 OLE 感知的应用程序公开 OLE 控件的接口。 如果将公开一个或多个接口，则每个 OLE 控件都必须具有类型库。

下列宏允许 OLE 控件提供对其自己的类型库的访问：

### <a name="type-library-access"></a>类型库访问

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|声明 OLE 控件（必须用于类声明中）的 `GetTypeLib` 成员函数。|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|实现 OLE 控件（必须用于类实现中）的 `GetTypeLib` 成员函数。|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

声明控件类`GetTypeLib`的成员函数。

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
与类型库相关的控件类的名称。

### <a name="remarks"></a>备注

在控件类标头文件中使用此宏。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

实现控件的成员`GetTypeLib`函数。

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>参数

*class_name*<br/>
与类型库相关的控件类的名称。

*tlid*<br/>
类型库的 ID 号。

*wVerMajor*<br/>
类型库主要版本号。

*wVerMinor*<br/>
类型库次要版本号。

### <a name="remarks"></a>备注

对于使用DECLARE_OLETYPELIB宏的任何控制类，此宏必须出现在实现文件中。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
