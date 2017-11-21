---
title: "从 CDocument 派生文档类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8f9152384522725dc932d0ce5e1c4cc81827160b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="deriving-a-document-class-from-cdocument"></a>从 CDocument 派生文档类
文档包含并管理你的应用程序数据。 若要使用的 MFC 应用程序向导提供的文档类，必须执行以下操作：  
  
-   从派生类**CDocument**每种类型的文档。  
  
-   添加成员变量以存储每个文档的数据。  
  
-   重写**CDocument**的`Serialize`成员函数在您的文档类。 `Serialize`写入和读取文档的数据传入和传出磁盘。  
  
## <a name="other-document-functions-often-overridden"></a>经常重写其他文档函数  
 你可能还想要重写其他**CDocument**成员函数。 具体而言，通常将需要重写[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)和[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)文档的数据成员进行初始化和[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)销毁动态分配的数据。 有关可重写的成员的信息，请参阅类[CDocument](../mfc/reference/cdocument-class.md)中*MFC 参考*。  
  
## <a name="see-also"></a>另请参阅  
 [使用文档](../mfc/using-documents.md)

