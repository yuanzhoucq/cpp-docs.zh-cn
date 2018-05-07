---
title: 类型的 MFC 类对象的转换 |Microsoft 文档
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
ms.openlocfilehash: 217be53a78a65a0f617438127b922b20c950853d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 类对象的类型强制转换
类型强制转换宏提供一种方法将给定的指针到指向特定类，使用或不检查转换合法的对象的指针转换。  
  
 下表列出了 MFC 类型强制转换宏。  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>强制转换与 MFC 类对象的指针的宏  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|检查以查看强转换是否合法时，将强制转换为指向类对象的指针。|  
|[STATIC_DOWNCAST](#static_downcast)|从一个类的指针的指针相关类型的指针转换到的对象。 在调试版本，会导致**断言**如果的对象不是"类型的"目标类型。|  
  
##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST  
 提供便捷途径，检查以查看强转换是否合法时强制转换为指向类对象的指针。  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>参数  
 `class`  
 类的名称。  
  
 `pointer`  
 若要强制转换为指向类型的对象的指针的指针`class`。  
  
### <a name="remarks"></a>备注  
 宏将强制转换`pointer`参数指向的对象的指针`class`参数的类型。  
  
 如果指针所引用的对象"类型的"标识的类，该宏将返回相应的指针。 如果它不是合法的转换，则该宏将返回**NULL**。  
  
##  <a name="static_downcast"></a>  STATIC_DOWNCAST  
 强制转换*pobject*的指针到*class_name*对象。  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>参数  
 *class_name*  
 要强制转换为类的名称。  
  
 *pobject*  
 要强制转换为指向的指针的指针*class_name*对象。  
  
### <a name="remarks"></a>备注  
 *pobject*必须**NULL**，或指向的对象直接派生的类或间接从*class_name*。 在与应用程序的生成 **_DEBUG**定义预处理器符号，该宏将**断言**如果*pobject*不**NULL**，或如果它指向的对象不是"类型的"中指定的类*class_name*参数 (请参阅[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof))。 在非 **_DEBUG**生成，宏执行强制转换，且无任何类型检查。  
  
 在指定的类*class_name*参数必须派生自`CObject`，并且必须使用`DECLARE_DYNAMIC`和`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏文章中所述[CObject 类： 从 CObject 派生类](../../mfc/deriving-a-class-from-cobject.md)。  
  
 例如，可能强制转换为指针`CMyDoc`、 调用`pMyDoc`的指针到**CDocument**使用以下表达式：  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 如果`pMyDoc`不指向对象直接或间接派生自**CDocument**，宏将**断言**。  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
