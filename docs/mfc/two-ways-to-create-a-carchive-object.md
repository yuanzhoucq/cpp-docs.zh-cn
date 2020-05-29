---
title: 创建 CArchive 对象的两种方法
ms.date: 11/04/2016
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
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370947"
---
# <a name="two-ways-to-create-a-carchive-object"></a>创建 CArchive 对象的两种方法

可通过两种方法创建 `CArchive` 对象：

- [通过框架隐式创建 CArchive 对象](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [显式创建 CArchive 对象](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>通过框架隐式创建 CArchive 对象

最常见和最简单的方法是让框架代表"文件"菜单上的"保存`CArchive`"、"保存为"和"打开"命令为文档创建对象。

下面是当应用程序的用户从"文件"菜单中发出"保存为"命令时，框架的作用：

1. 显示"**另存为"** 对话框并从用户获取文件名。

1. 打开用户命名的`CFile`对象文件。

1. 创建指向`CArchive`此`CFile`对象的对象。 在创建对象`CArchive`时，框架将模式设置为"存储"（写入、序列化），而不是"加载"（读取、反序列化）。

1. 调用派生`Serialize`类中`CDocument`定义的函数，将其传递给`CArchive`对象的引用。

然后，文档的功能`Serialize`将数据写入`CArchive`对象，如稍后所述。 从函数`Serialize`返回后，框架将销毁`CArchive`对象，然后销毁`CFile`该对象。

因此，如果让框架为文档创建`CArchive`对象，则所有要做的就是实现文档的`Serialize`函数，该函数在存档中写入和读取。 您还必须`Serialize`实现文档`CObject``Serialize`函数反过来直接或间接序列化的任何派生对象。

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>显式创建 CArchive 对象

除了通过框架序列化文档外，还有其他可能需要`CArchive`对象的情况。 例如，您可能希望序列化数据，并从剪贴板（由`CSharedFile`对象表示）进行序列化。 或者，您可能希望使用用户界面保存与框架提供的文件不同的文件。 在这种情况下，您可以显式创建对象`CArchive`。 使用以下过程，使用框架相同的方式执行此操作。

#### <a name="to-explicitly-create-a-carchive-object"></a>显式创建 CArchive 对象

1. 构造派生`CFile`自`CFile`的对象或对象。

1. 将`CFile`对象传递给 的`CArchive`构造函数，如以下示例所示：

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   `CArchive`构造函数的第二个参数是枚举值，该值指定存档是否将用于存储或加载数据到文件或从文件中加载数据。 对象的`Serialize`函数通过调用存档对象的`IsStoring`函数来检查此状态。

完成存储或加载数据到或从对象加载后，`CArchive`关闭它。 尽管`CArchive`（和`CFile`） 对象将自动关闭存档（和文件），但最好显式关闭存档（和 文件），因为它使从错误中恢复更容易。 有关错误处理的详细信息，请参阅文章["例外：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)"。

#### <a name="to-close-the-carchive-object"></a>关闭 CArchive 对象

1. 下面的示例说明了如何关闭`CArchive`对象：

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
