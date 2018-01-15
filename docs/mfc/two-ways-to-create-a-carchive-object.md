---
title: "创建 CArchive 对象两种方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CArchive
dev_langs: C++
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b1db549544d421600ed6dae1a8a987006c2ab6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="two-ways-to-create-a-carchive-object"></a>创建 CArchive 对象的两种方法
可通过两种方法创建 `CArchive` 对象：  
  
-   [隐式创建框架通过 CArchive 对象](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [显式创建 CArchive 对象](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>隐式创建框架通过 CArchive 对象  
 最常见的且最简单，方法是让创建的框架`CArchive`保存、 另存为和文件菜单上的打开命令代表文档的对象。  
  
 下面是框架时你的应用程序的用户发出文件菜单中的另存为命令的用途：  
  
1.  显示**另存为**对话框中，并从用户获取文件名。  
  
2.  将打开由作为用户命名的文件`CFile`对象。  
  
3.  创建`CArchive`指向此对象`CFile`对象。 在创建`CArchive`对象，该框架将模式设置"存储"（写入、 序列化），而不是"负载"（读取、 反序列化）。  
  
4.  调用`Serialize`函数中定义你**CDocument**-派生类，将其传递到的引用`CArchive`对象。  
  
 文档的`Serialize`函数然后可将数据写入`CArchive`对象，稍后所述。 返回从后你`Serialize`函数，框架会销毁`CArchive`对象，然后`CFile`对象。  
  
 因此，如果你让创建的框架`CArchive`对象对于你的文档，所要做是实现文档的`Serialize`写入和读取到和从存档的函数。 你还必须实现`Serialize`任何`CObject`-派生对象的文档的`Serialize`直接或间接函数反过来序列化。  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a>显式创建 CArchive 对象  
 除了通过该框架将文档序列化，有可能需要其他情况下`CArchive`对象。 例如，你可能想要序列化数据传入和传出剪贴板，由表示`CSharedFile`对象。 或者，你可能想要用于保存从框架所提供的一个不同的文件的用户界面。 在这种情况下，你可以显式创建`CArchive`对象。 你执行此相同的方式框架执行的操作，使用以下过程。  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>若要显式创建 CArchive 对象  
  
1.  构造`CFile`对象派生自`CFile`。  
  
2.  传递`CFile`为构造函数的对象`CArchive`，下面的示例中所示：  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     第二个参数`CArchive`构造函数是一个枚举的值，指定是否将用于从文件存储或加载数据到或使用存档。 `Serialize`对象的函数调用通过检查此状态`IsStoring`存档对象的函数。  
  
 在存储或加载到或者来自数据完成时`CArchive`对象，请关闭它。 尽管`CArchive`(和`CFile`) 的存档 （和文件），对象将自动关闭，则你最好显式执行操作，因为这会从错误恢复更容易。 有关错误处理的详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
#### <a name="to-close-the-carchive-object"></a>若要关闭 CArchive 对象  
  
1.  下面的示例演示如何关闭`CArchive`对象：  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)

