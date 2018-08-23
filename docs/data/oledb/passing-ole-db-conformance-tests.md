---
title: 通过 OLE DB 一致性测试 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0288e1517bf89ec6ff8a2067311c3641d8d7113c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340911"
---
# <a name="passing-ole-db-conformance-tests"></a>通过 OLE DB 一致性测试
为了使提供程序更加一致，数据访问 SDK 提供了一组 OLE DB 一致性测试。 测试检查您的提供程序的所有方面，并为你提供合理的保证，在提供程序按预期方式运行。 您可以在 Microsoft 数据访问 SDK 中找到 OLE DB 一致性测试。 本部分重点介绍应执行通过一致性测试的操作。 有关正在运行的 OLE DB 一致性测试的信息，请参阅 SDK。  
  
## <a name="running-the-conformance-tests"></a>运行一致性测试  
 在 Visual c + + 6.0 中，OLE DB 提供程序模板添加了大量挂钩函数，以使你能够检查值和属性。 其中的大多数功能已添加以响应对符合性测试。  
  
> [!NOTE]
>  您需要添加多个验证函数，以使提供程序通过 OLE DB 一致性测试。  
  
 此提供程序需要两个验证例程。 第一个例程， `CRowsetImpl::ValidateCommandID`，是行集类的一部分。 它是由提供程序模板调用在行集的创建过程。 此示例使用此例程来告诉使用者不支持索引。 第一个调用是对`CRowsetImpl::ValidateCommandID`(请注意，在提供程序使用`_RowsetBaseClass`添加的接口映射中的 typedef`CMyProviderRowset`中[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)，因此无需键入模板的长行自变量）。 接下来，返回 DB_E_NOINDEX，如果索引参数不为 NULL （指示使用者想要使用我们的索引）。 有关命令 Id 的详细信息，请参阅 OLE DB 规范，并查找`IOpenRowset::OpenRowset`。  
  
 下面的代码是`ValidateCommandID`验证例程：  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)  
{  
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);  
   if (hr != S_OK)  
      return hr;  
  
   if (pIndexID != NULL)  
      return DB_E_NOINDEX;    // Doesn't support indexes  
  
   return S_OK;  
}  
```  
  
 提供程序模板调用`OnPropertyChanged`方法，只要有人更改某个属性上`DBPROPSET_ROWSET`组。 如果你想要处理的其他组的属性，您将它们添加到适当的对象 (即`DBPROPSET_SESSION`检查进入`CMyProviderSession`类)。  
  
 代码首先检查以查看是否链接到另一个属性。 如果链接属性，它会设置`DBPROP_BOOKMARKS`属性设为 True。 OLE DB 规范的附录 C 包含有关属性的信息。 此信息还将告诉您是否将属性链接到另一个。  
  
 您可能还想要添加`IsValidValue`到你的代码例程。 模板调用`IsValidValue`时尝试设置属性。 如果需要额外的处理设置的属性值时，会重写此方法。 您可以为每个属性集的下列方法之一。  
  
## <a name="threading-issues"></a>线程处理问题  
 默认情况下，OLE DB 提供程序中的向导在 ATL OLE DB 提供程序向导生成要在单元模型中运行的提供程序的代码。 如果你尝试运行此代码使用符合性测试，开始就会失败。 这是因为 Ltm.exe，用来运行 OLE DB 一致性测试，该工具默认为自由线程的。 OLE DB 提供程序向导代码将默认为单元模型的性能和易用性。  
  
 若要更正此问题，可以更改 LTM 或更改的提供程序。  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>LTM 改为单元中运行线程模式  
  
1.  LTM 主菜单上，单击**工具**，然后单击**选项**。  
  
2.  上**常规**选项卡上，将从该线程处理模型更改**自由线程**到**Apartment Threaded**。  
  
 若要更改您的提供商在可用的线程模式下运行：  
  
-   在提供程序项目中，搜索的所有实例`CComSingleThreadModel`并将其替换为`CComMultiThreadModel`，应在数据源、 会话和行集标头中。  
  
-   在.rgs 文件中，将更改从线程模型**单元**到**同时**。  
  
-   遵循正确编程规则免费线程的编程 （即，写入锁定）。  
  
## <a name="see-also"></a>请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)