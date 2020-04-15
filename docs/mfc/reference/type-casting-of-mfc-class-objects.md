---
title: MFC 类对象的类型强制转换
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372891"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 类对象的类型强制转换

类型转换宏提供了一种将给定指针转换为指向特定类对象的指针的方法，无论是否检查强制转换是否合法。

下表列出了 MFC 类型强制转换宏。

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>向 MFC 类对象强制转换指针的宏

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|在检查强制转换是否合法时，将指向类对象的指针强制转换。|
|[STATIC_DOWNCAST](#static_downcast)|将指向对象的指针从一个类转换为相关类型的指针。 在调试生成中，如果对象不是目标类型的"类型"，则会导致 ASSERT。|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

提供了一种方便的方法，用于在检查强制转换是否合法时，将指向类对象的指针转换为指针。

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>参数

*class*<br/>
类的名称。

*指针 (pointer)*<br/>
要转换为指向类型*类*对象的指针的指针。

### <a name="remarks"></a>备注

宏将*指针*参数转换为指向*类*参数类型对象的指针。

如果指针引用的对象是标识的类的"类型"，则宏将返回相应的指针。 如果它不是法定强制转换，宏将返回 NULL。

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

将*pobject*投射到指向*class_name*对象的指针。

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>参数

*class_name*<br/>
要强制转换到的类的名称。

*pobject*<br/>
要转换为指向*class_name*对象的指针。

### <a name="remarks"></a>备注

*pobject*必须是 NULL，或者指向直接从或间接派生自*class_name*的类的对象。 在定义了_DEBUG预处理器符号的应用程序的版本中，如果*pobject*不是 NULL，或者如果它指向不是*class_name*参数中指定的类的"类型"的对象（请参阅[CObject：IsKindOf），](../../mfc/reference/cobject-class.md#iskindof)宏将断言。 在非 **_DEBUG**生成中，宏执行强制转换，无需进行任何类型检查。

*class_name*参数中指定的类必须派生自`CObject`，并且必须使用DECLARE_DYNAMIC和IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE和IMPLEMENT_DYNCREATE，或者DECLARE_SERIAL和IMPLEMENT_SERIAL宏，如[CObject 类中的说明：从 CObject 派生类](../../mfc/deriving-a-class-from-cobject.md)。

例如，您可以将指针转换为`CMyDoc``pMyDoc`调用 的 指针，指向`CDocument`使用此表达式的指针：

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

如果不`pMyDoc`指向直接或间接派生的对象`CDocument`，宏将断言。

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
