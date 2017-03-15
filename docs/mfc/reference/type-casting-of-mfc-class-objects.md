---
title: "类型的 MFC 类对象的转换 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros, type casting
- pointers, type casting
- type casts
- casting types
- macros, casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f1ae094e7085017f03daab3f73323da13ab1be39
ms.lasthandoff: 02/24/2017

---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 类对象的类型强制转换
类型强制转换宏提供了一种方法将给定的指针到指向特定的类，无论有检查转换合法的对象的指针转换。  
  
 下表列出了 MFC 类型强制转换宏。  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>强制转换到 MFC 类对象的指针的宏  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|检查以查看该强制转换是否合法时转换为指向类对象的指针。|  
|[STATIC_DOWNCAST](#static_downcast)|将一个指针，到对象从一个类的指针的指针的相关类型强制转换。 在调试版本中，将导致**ASSERT**如果对象不是"类型的"目标类型。|  
  
##  <a name="a-namedynamicdowncasta--dynamicdowncast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST  
 提供了检查以查看该强制转换是否合法时强制转换为指向类对象的指针的便捷途径。  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>参数  
 `class`  
 类的名称。  
  
 `pointer`  
 若要强制转换为指向类型的对象的指针的指针`class`。  
  
### <a name="remarks"></a>备注  
 该宏将强制转换`pointer`参数指向的对象的指针`class`参数的类型。  
  
 如果指针引用的对象"类型的"标识的类，该宏将返回相应的指针。 如果不是合法的转换，该宏将返回**NULL**。  
  
##  <a name="a-namestaticdowncasta--staticdowncast"></a><a name="static_downcast"></a>STATIC_DOWNCAST  
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
 *pobject*必须将**NULL**，或指向的对象的类中派生出来，直接或间接从*class_name*。 在与应用程序的生成**_DEBUG**定义预处理器符号后，该宏将**ASSERT**如果*pobject*不是**NULL**，或如果它指向一个对象，不是"类型的"中指定的类*class_name*参数 (请参阅[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof))。 在非**_DEBUG**版本中，该宏执行不进行任何类型检查的强制转换。  
  
 中指定的类*class_name*参数必须派生自`CObject`，并且必须使用`DECLARE_DYNAMIC`和`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏文章中所述[CObject 类︰ 从 CObject 派生类](../../mfc/deriving-a-class-from-cobject.md)。  
  
 例如，可能会强制转换为指针`CMyDoc`，称为`pMyDoc`的指针到**CDocument**使用以下表达式︰  
  
 [!code-cpp[NVC_MFCDocView #&197;](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 如果`pMyDoc`不指向对象直接或间接派生自**CDocument**，该宏将**ASSERT**。  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

