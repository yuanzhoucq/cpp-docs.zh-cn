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
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442036"
---
# <a name="two-ways-to-create-a-carchive-object"></a>创建 CArchive 对象的两种方法

可通过两种方法创建 `CArchive` 对象：

- [通过框架隐式创建 CArchive 对象](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [显示 CArchive 对象的显式创建](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>通过框架隐式创建 CArchive 对象

最常见、最简单的方法是让框架代表 "文件" 菜单上的 "保存"、"另存为" 和 "打开" 命令为文档创建一个 `CArchive` 对象。

下面是当应用程序的用户从 "文件" 菜单发出 "另存为" 命令时，框架的作用：

1. 显示 "**另存为**" 对话框，并从用户获取文件名。

1. 以 `CFile` 对象的形式打开用户指定的文件。

1. 创建一个指向此 `CFile` 对象的 `CArchive` 对象。 在创建 `CArchive` 对象时，框架会将模式设置为 "存储" （写入、序列化），而不是 "加载" （读取、反序列化）。

1. 调用 `CDocument`派生类中定义的 `Serialize` 函数，并向其传递对 `CArchive` 对象的引用。

文档的 `Serialize` 函数随后将数据写入 `CArchive` 对象，如稍后所述。 从 `Serialize` 函数返回后，框架会销毁 `CArchive` 对象，然后销毁 `CFile` 对象。

因此，如果你让框架为你的文档创建 `CArchive` 对象，则只需实现文档的 `Serialize` 函数，该函数可在存档中写入和读取数据。 还必须为文档的 `Serialize` 函数反过来直接或间接序列化的任何 `CObject`派生对象实现 `Serialize`。

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>显示 CArchive 对象的显式创建

除了通过框架序列化文档外，还有其他一些可能需要 `CArchive` 对象的情况。 例如，你可能想要将数据序列化到剪贴板，并从剪贴板中序列化，由 `CSharedFile` 对象表示。 或者，您可能想要使用用户界面保存与框架提供的文件不同的文件。 在这种情况下，可以显式创建 `CArchive` 对象。 您可以使用以下过程通过与框架相同的方式来执行此操作。

#### <a name="to-explicitly-create-a-carchive-object"></a>显式创建 CArchive 对象

1. 构造 `CFile` 对象或派生自 `CFile`的对象。

1. 将 `CFile` 对象传递到 `CArchive`的构造函数，如以下示例中所示：

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   `CArchive` 构造函数的第二个参数是一个枚举值，该值指定是否将存档用于在文件中存储数据或从文件中加载数据。 对象的 `Serialize` 函数通过为 archive 对象调用 `IsStoring` 函数来检查此状态。

当你完成将数据存储到 `CArchive` 对象或从该对象加载数据时，请将其关闭。 尽管 `CArchive` （和 `CFile`）对象会自动关闭存档（和文件），但最好显式这样做，因为这样可以更轻松地从错误中恢复。 有关错误处理的详细信息，请参阅文章[异常：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

#### <a name="to-close-the-carchive-object"></a>关闭 CArchive 对象

1. 下面的示例演示如何关闭 `CArchive` 对象：

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>另请参阅

[序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)
