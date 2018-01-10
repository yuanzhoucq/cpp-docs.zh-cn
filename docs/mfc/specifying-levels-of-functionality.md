---
title: "指定功能级别 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13a2897d5e442794198870e7f6bed36196744888
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-levels-of-functionality"></a>指定功能级别
本文介绍如何将添加到的功能的以下级别你[CObject](../mfc/reference/cobject-class.md)-派生类：  
  
-   [运行时类信息](#_core_to_add_run.2d.time_class_information)  
  
-   [动态创建支持](#_core_to_add_dynamic_creation_support)  
  
-   [序列化支持](#_core_to_add_serialization_support)  
  
 有关常规说明`CObject`功能，请参阅文章[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)。  
  
-   [运行时类信息](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a>若要添加运行时类信息  
  
1.  派生您的类从`CObject`中所述，[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)文章。  
  
2.  使用`DECLARE_DYNAMIC`宏的类声明，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  使用`IMPLEMENT_DYNAMIC`实现文件中的宏 (。CPP) 的您的类。 此宏将作为自变量类和其基本类的名称，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  始终将放`IMPLEMENT_DYNAMIC`在实现文件 (。CPP) 为您的类。 `IMPLEMENT_DYNAMIC`宏应在编译期间一次计算，并因此不应使用在接口文件 (。H），可可能包括在多个文件。  
  
#### <a name="_core_to_add_dynamic_creation_support"></a>若要添加动态创建支持  
  
1.  派生您的类从`CObject`。  
  
2.  使用`DECLARE_DYNCREATE`类声明中的宏。  
  
3.  定义没有自变量 （默认构造函数） 的构造函数。  
  
4.  使用`IMPLEMENT_DYNCREATE`类实现文件中的宏。  
  
#### <a name="_core_to_add_serialization_support"></a>若要添加序列化支持  
  
1.  派生您的类从`CObject`。  
  
2.  重写`Serialize`成员函数。  
  
    > [!NOTE]
    >  如果调用`Serialize`直接，也就是说，您不想要通过多态指针将对象序列化、 省略步骤 3 至 5。  
  
3.  使用`DECLARE_SERIAL`类声明中的宏。  
  
4.  定义没有自变量 （默认构造函数） 的构造函数。  
  
5.  使用`IMPLEMENT_SERIAL`类实现文件中的宏。  
  
> [!NOTE]
>  "多态指针"指向类的对象 (调用它的) 或派生自 （比如，B） 的任何类的对象。 若要通过多态指针序列化，框架必须确定它序列化 (B)，因为它可能是派生自一些基类 (A) 的任何类的对象的对象的运行时类。  
  
 有关如何从您的类派生时启用序列化的详细信息`CObject`，请参阅文章[MFC 中的文件](../mfc/files-in-mfc.md)和[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)
