---
title: OLE DB 结构设计问题
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: ef2837ea80c61f074cf567ee1fe61fa2cfa0ae73
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525308"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 结构设计问题

> [!NOTE]
> ATL OLE DB 使用者向导不适用于 Visual Studio 2019 及更高版本。 但仍可以手动添加此功能。 有关详细信息，请参阅[不使用向导创建使用者](creating-a-consumer-without-using-a-wizard.md)。

开始创建 OLE DB 应用程序前，请先考虑以下问题：

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>将使用什么编程实现来编写 OLE DB 应用程序？

Microsoft 提供了多个可完成此任务的库：OLE DB 模板库、OLE DB 特性和 OLE DB SDK 中的原始 OLE DB 接口。 此外，还有一些向导可帮助你编写程序。 [OLE DB 模板、特性和其他实现](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)中介绍了这些实现。

## <a name="do-you-need-to-write-your-own-provider"></a>是否需要编写你自己的提供程序？

大多数开发人员无需编写自己的提供程序。 Microsoft 提供了多个提供程序。 每当你创建数据连接时（例如，当你使用 ATL OLE DB 使用者向导将使用者添加到项目时），“数据链接属性”对话框都会列出系统中的所有已注册提供程序。 如果其中一个提供程序适用于你自己的数据存储和数据访问应用程序，最简单的办法就是使用其中一个。 不过，如果数据存储不适合这些类别之一，就必须创建你自己的提供程序。 若要了解如何创建提供程序，请参阅 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)。

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>需要对使用者使用何种支持级别？

一些使用者可能是基本的，而另一些使用者则可能是复杂的。 OLE DB 对象的功能由属性指定。 如果你使用 ATL OLE DB 使用者向导创建使用者，或使用数据库提供程序向导创建提供程序，它会为你设置适当的对象属性，以提供一组标准功能。 不过，如果向导生成的使用者类或提供程序类不支持你需要它们执行的任何操作，必须引用 [OLE DB 模板库](../../data/oledb/ole-db-templates.md)中这些类的接口。 这些接口包装原始 OLE DB 接口，提供额外实现来让它们更易于使用。

例如，若要更新行集中的数据，但在使用向导创建使用者时忘记了指定这样做，可以通过对命令对象设置 `DBPROP_IRowsetChange` 和 `DBPROP_UPDATABILITY` 属性，在事后指定功能。 然后，创建的行集就包含 `IRowsetChange` 接口了。

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>你是否有使用其他数据访问技术（ADO、ODBC 或 DAO）的旧代码？

鉴于可能的技术组合（如结合使用 ADO 组件与 OLE DB 组件，以及将 ODBC 代码迁移到 OLE DB），涵盖所有情况超出了 Visual C++ 文档的范围。 不过，以下 Microsoft 网站提供了许多涵盖各种情况的文章：

- [Microsoft 帮助和支持](https://support.microsoft.com/)

- [Microsoft 数据访问技术文章概述](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
