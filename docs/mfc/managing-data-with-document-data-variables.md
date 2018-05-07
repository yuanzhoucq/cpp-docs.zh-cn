---
title: 使用文档数据变量管理数据 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8048a38c2ec09828c462d5b671cc0c89aec30805
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="managing-data-with-document-data-variables"></a>使用文档数据变量管理数据
实现文档的数据为您的文档类的成员变量。 例如，Scribble 程序声明类型的数据成员`CObList`-存储指向的链接的列表`CObject`对象。 此列表用于存储的构成画线条图形的点数组。  
  
 实现文档的成员数据的方式取决于你的应用程序的性质。 为了帮助你出，MFC 还提供的一组"集合类"-数组、 列表和映射 （字典），包括基于 c + + 模板的集合，如封装各种常见数据类型的类以及`CString`， `CRect`， `CPoint`， `CSize`，和`CTime`。 有关这些类的详细信息，请参阅[类库概述](../mfc/class-library-overview.md)中*MFC 参考*。  
  
 在定义文档的成员数据时，你通常将到文档类，以设置和获取数据项以及执行其他有用的操作在其上添加成员函数。  
  
 您的视图通过使用到文档中，安装在创建时视图中的视图的指针访问文档对象。 您可以通过调用来检索视图的成员函数中的此指针`CView`成员函数**GetDocument**。 请务必将该指针为你自己的文档类型转换。 然后你可以通过指针访问公共文档成员。  
  
 如果频繁的数据传输需要直接访问，或你想要使用的文档类的非公共成员，你可能想要使视图类 （在 c + + 条款） 的文档类的友元。  
  
## <a name="see-also"></a>请参阅  
 [使用文档](../mfc/using-documents.md)

