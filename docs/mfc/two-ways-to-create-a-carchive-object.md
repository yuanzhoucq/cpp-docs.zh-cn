---
title: 创建 CArchive 对象的两种方法
ms.date: 11/04/2016
f1_keywords:
- CArchive
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
ms.openlocfilehash: 80e3e73840bce53691c3f5fdafb62c60bdb8f832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181505"
---
# <a name="two-ways-to-create-a-carchive-object"></a>创建 CArchive 对象的两种方法

可通过两种方法创建 `CArchive` 对象：

- [隐式创建 CArchive 对象通过框架](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [显式创建 CArchive 对象](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 隐式创建 CArchive 对象通过框架

最常见且最简单的方法是让框架来创建`CArchive`保存、 另存为，并在文件菜单上的打开命令代表文档的对象。

下面是框架应用程序的用户发出文件菜单中的另存为命令时的用途：

1. 提供了**另存为**对话框中，并从用户获取文件名。

1. 打开文件的用户作为名为`CFile`对象。

1. 创建`CArchive`指向此对象`CFile`对象。 在创建`CArchive`对象时，框架将设置模式"存储"（写入、 序列化），而不是"加载"（读取、 反序列化）。

1. 调用`Serialize`函数中定义你`CDocument`-派生的类，并向其传递到引用`CArchive`对象。

您的文档`Serialize`函数然后将数据写入`CArchive`对象，如稍后所述。 返回从时你`Serialize`函数，该框架会销毁`CArchive`对象，然后`CFile`对象。

因此，如果让框架创建`CArchive`对象的文档，只需是实现文档的`Serialize`写入和读取到和从存档的函数。 您还必须实现`Serialize`任何`CObject`-派生的对象的文档的`Serialize`函数直接或间接反过来将序列化。

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> 显式创建 CArchive 对象

除了通过框架将文档序列化，在时可能需要其他场合`CArchive`对象。 例如，你可能想要序列化数据传入和传出剪贴板，由表示`CSharedFile`对象。 或者，你可能想要用于保存的文件，由框架提供的一个不同的用户界面。 在这种情况下，可以显式创建`CArchive`对象。 为此的相同框架执行的操作，使用以下过程。

#### <a name="to-explicitly-create-a-carchive-object"></a>若要显式创建 CArchive 对象

1. 构造`CFile`对象派生自`CFile`。

1. 传递`CFile`对象的构造函数与`CArchive`，如以下示例所示：

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   第二个参数`CArchive`构造函数是一个枚举的值，指定是否将用于从文件存储或加载数据或使用存档。 `Serialize`函数的对象通过调用检查此状态`IsStoring`存档对象函数。

完成后，存储或加载数据传入或传出`CArchive`对象，请关闭它。 尽管`CArchive`(和`CFile`) 存档 （和文件），会自动关闭对象，它是很好的做法显式执行操作，因为它可从错误中的恢复更轻松。 有关错误处理的详细信息，请参阅文章[异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

#### <a name="to-close-the-carchive-object"></a>若要关闭 CArchive 对象

1. 下面的示例演示如何关闭`CArchive`对象：

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>请参阅

[序列化：序列化对象](../mfc/serialization-serializing-an-object.md)
