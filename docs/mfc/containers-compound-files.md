---
title: 容器：复合文件
ms.date: 11/04/2016
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
ms.openlocfilehash: 98166a355fd267ecbec0a7f0cc1d18fd0b2e7cd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353591"
---
# <a name="containers-compound-files"></a>容器：复合文件

本文介绍了复合文件的组件和实现以及在 OLE 应用程序中使用复合文件的优缺点。

复合文件是 OLE 的组成部分。 它们用于促进数据传输和 OLE 文档存储。 复合文件是活动结构化存储模型的实现。 存在支持存储、流或文件对象的序列化的一致接口。 复合文件在 Microsoft 基础类库中受 `COleStreamFile` 和 `COleDocument` 这两个类的支持。

> [!NOTE]
> 使用复合文件并不暗指信息来自 OLE 文档或复合文档。 复合文件只是一种存储复合文档、OLE 文档和其他数据的方式。

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>复合文件的组件

复合文件的 OLE 实现使用 3 种对象类型：流对象、存储对象和 `ILockBytes` 对象。 这些对象在下列方面类似于标准文件系统的组件：

- 流对象（如文件）存储任何类型的数据。

- 存储对象（如目录）可以包含其他存储和流对象。

- `LockBytes`对象表示存储对象和物理硬件之间的接口。 它们确定如何将实际字节写入`LockBytes`对象正在访问的任何存储设备，如硬盘驱动器或全局内存区域。 有关`LockBytes`对象和接口的详细信息，`ILockBytes`请参阅 OLE*程序员的参考*。

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>复合文件的优缺点

复合文件提供了之前的文件存储方式不具备的好处。 其中包括：

- 增量文件访问。

- 文件访问模式。

- 文件结构的标准化。

确定是否在应用程序中使用复合文件时，应考虑复合文件的潜在劣势 - 规模大以及与软光盘存储有关的性能问题。

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>对文件的增量访问

对文件的增量访问是使用复合文件必然的好处。 由于复合文件可作为“文件中的文件系统”、独立对象类型（如流或存储）查看，因此访问时无需加载整个文件。 这可以显著减少应用程序访问用户要编辑的新对象所需的时间。 根据同一概念，增量更新将提供类似的好处。 OLE 将仅保存用户编辑的流或存储对象，而不是保存整个文件只为了保存对一个对象所做的更改。

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>文件访问模式

能够确定何时将对复合文件中对象的更改提交给磁盘是使用复合文件的另一个好处。 文件的访问模式（事务处理或直接）将确定更改的提交时间。

- 事务处理模式使用两段提交操作来更改复合文件中的对象，从而在用户选择保存或撤销更改之前，一直保持文档的新旧副本可用。

- 直接模式在更改文档时合并所做更改，这些更改之后无法撤销。

有关访问模式的详细信息，请参阅 OLE*程序员的参考*。

### <a name="standardization"></a><a name="_core_standardization"></a>标准化

复合文件的标准结构使不同的 OLE 应用程序可浏览 OLE 应用程序创建的复合文件，而不必了解实际创建文件的应用程序。

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>大小和性能注意事项

由于复合文件存储结构的复杂和增量保存数据的功能，使用此格式的文件可能大于使用无结构或“平面文件”存储的其他文件。 如果应用程序频繁加载和保存文件，则使用复合文件可能导致文件大小的增加速度比非复合文件的快得多。 由于复合文件会增大，因此存储在软光盘和从软光盘加载的文件的访问时间也会受影响，从而导致对文件的访问更慢。

影响性能的另一个问题是复合文件碎片。 复合文件的大小由文件使用的第一个和最后一个磁盘扇区之间的差异确定。 零碎的文件可包含可用空间中不包含数据、但在计算大小时会进行计数的许多区域。 在复合文件的生存期内，这些区域将通过插入或删除存储对象来创建。

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>对数据使用复合文件格式

在成功创建文档类派生自 `COleDocument` 的应用程序之后，确保您的主文档构造函数调用 `EnableCompoundFile`。 应用程序向导创建 OLE 容器应用程序之后，将为您插入此调用。

在*OLE 程序员的参考中*，请参阅[IStream、IStorage](/windows/win32/api/objidl/nn-objidl-istream)和[ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes)。 [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)

## <a name="see-also"></a>另请参阅

[容器](../mfc/containers.md)<br/>
[容器：用户界面问题](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile 类](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument 类](../mfc/reference/coledocument-class.md)
