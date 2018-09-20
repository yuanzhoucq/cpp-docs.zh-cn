---
title: 类型的 MFC 类对象的显式转换 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f459f1cad1b863f0c96e9c885fd2c54831d6b6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382435"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 类对象的类型强制转换

类型强制转换宏提供一种方法来转换给定的指针到指向特定类，使用或不检查强制转换合法的对象的指针。

下表列出了 MFC 类型强制转换宏。

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>强制转换到 MFC 类对象的指针的宏

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|检查以查看强转换是否合法时，将强制转换为指向类对象的指针。|
|[STATIC_DOWNCAST](#static_downcast)|将指针的对象从一个类的指针的指针的相关类型强制转换。 在调试版本中，如果将导致断言的对象不是"类型的"目标类型。|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

提供了方便地检查以查看强转换是否合法时转换为指向类对象的指针。

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>参数

*class*<br/>
类的名称。

*pointer*<br/>
若要强制转换为指向类型的对象的指针的指针*类*。

### <a name="remarks"></a>备注

该宏将强制转换*指针*指向的对象的指针参数*类*参数的类型。

如果指针所引用的对象"类型的"标识的类，该宏将返回相应的指针。 如果它不是合法的转换，该宏将返回 NULL。

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

强制转换*pobject*指向的*class_name*对象。

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>参数

*class_name*<br/>
要强制转换为类的名称。

*pobject*<br/>
要强制转换为指向指针的指针*class_name*对象。

### <a name="remarks"></a>备注

*pobject*必须为 NULL，或者指向对象的直接派生的类或间接从*class_name*。 在应用程序定义 _DEBUG 预处理器符号的版本中，如果断言宏*pobject*不为 NULL，或如果它指向一个对象，不是"类型的"中指定的类*class_name*参数 (请参阅[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof))。 在非 **_DEBUG**版本中，该宏执行转换，而无需任何类型检查。

在指定的类*class_name*参数必须派生自`CObject`，并且必须使用 DECLARE_DYNAMIC 和 IMPLEMENT_DYNAMIC、 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE，或 DECLARE_SERIAL 和 IMPLEMENT_为串行宏一文中所述[CObject 类： 从 CObject 派生类](../../mfc/deriving-a-class-from-cobject.md)。

例如，可能会强制转换为指针`CMyDoc`，称为`pMyDoc`，为指向的`CDocument`使用此表达式：

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

如果`pMyDoc`不指向对象直接或间接派生自`CDocument`，宏将断言。

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
