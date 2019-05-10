---
title: 使用 CStringT 导出字符串类
ms.date: 11/04/2016
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
ms.openlocfilehash: a4ee73d2ae5cfb7bf9834fb23eed8470b7d29445
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252735"
---
# <a name="exporting-string-classes-using-cstringt"></a>使用 CStringT 导出字符串类

在过去，MFC 开发人员具有派生自`CString`专用化其自己的字符串类。 在 Microsoft 的视觉对象C++.NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md)类由一个名为模板类所取代[CStringT](../atl-mfc-shared/reference/cstringt-class.md)。 这提供以下几个好处：

- 它允许 MFC`CString`类用于 ATL 项目中的较大的 MFC 静态库或 DLL 链接的情况下。

- 与新`CStringT`你可以自定义模板类`CString`行为使用指定字符特征，类似于在模板的模板参数C++标准库。

- 当您从 DLL 使用导出字符串类`CStringT`，编译器还会自动将导出`CString`基类。 由于`CString`本身是一种模板类，它可能实例化，由编译器使用时，除非编译器已注意到，`CString`从 DLL 导入。 如果已从 Visual 迁移项目C++6.0 到 Visual C++.NET 中，您可以看到链接器的多重定义的符号错误`CString`由于的冲突`CString`导入从 DLL 和本地实例化的版本. 若要执行此操作的正确方法如下所述。

以下方案会导致链接器生成的符号错误多次定义的类。 假设您要导出`CString`的派生类 (`CMyString`) 从 MFC 扩展 DLL:

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

使用者代码使用的混合`CString`和`CMyString`。 "MyString.h"未包含在预编译标头和一些使用情况`CString`不具有`CMyString`可见。

假定您使用`CString`和`CMyString`Source1.cpp 和 Source2.cpp 单独的源代码文件中的类。 Source1.cpp，在您使用`CMyString`和 #include MyString.h。 Source2.cpp，在您使用`CString`，但却没有 #include MyString.h。 在这种情况下，链接器会抱怨`CStringT`被多次定义。 这由于`CString`正在从 DLL 导出的导入`CMyString`，并通过编译器的本地实例化`CStringT`模板。

若要解决此问题，请执行以下操作：

导出`CStringA`和`CStringW`（和必需的基本类） 从 MFC90。DLL。 包括 MFC 项目将始终使用 MFC DLL 导出`CStringA`和`CStringW`，如以前的 MFC 实现。

然后，创建可导出的派生的类使用`CStringT`模板，作为`CStringT_Exported`低于，例如：

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

在 AfxStr.h，替换以前`CString`， `CStringA`，和`CStringW`typedef，如下所示：

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

有几个需要注意的问题：

- 不应导出`CStringT`本身因为这会导致仅限 ATL 的项目将导出一个专用`CStringT`类。

- 使用可导出的派生类从`CStringT`最大程度减少无需重新实现`CStringT`功能。 额外的代码仅限于转发构造函数来`CStringT`基类。

- `CString``CStringA`，并`CStringW`应仅标记`__declspec(dllexport/dllimport)`您使用 MFC 的生成时共享 DLL。 如果链接 MFC 静态库，您应将标记这些类为导出;否则为内部使用`CString`， `CStringA`，和`CStringW`内部用户 Dll 会将标记`CString`也导出。

## <a name="related-topics"></a>相关主题

[CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>请参阅

[使用 CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[使用 CString](../atl-mfc-shared/using-cstring.md)
