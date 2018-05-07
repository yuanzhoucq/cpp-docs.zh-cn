---
title: 传递 OLE DB 一致性测试 |Microsoft 文档
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
ms.openlocfilehash: 11677e6295956de768c7ebc0c113d775b066bb0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="passing-ole-db-conformance-tests"></a>通过 OLE DB 一致性测试
为了使提供程序更为一致，数据访问 SDK 提供了一组 OLE DB 一致性测试。 这些测试检查你的提供商的所有方面，并为你提供合理你提供程序按预期方式运行的保证。 您可以在 Microsoft 数据访问 SDK 中找到 OLE DB 一致性测试。 本部分重点介绍应完成通过一致性测试任务。 有关运行 OLE DB 一致性测试的信息，请参阅 SDK。  
  
## <a name="running-the-conformance-tests"></a>运行一致性测试  
 在 Visual c + + 6.0 中，OLE DB 提供程序模板添加了大量挂钩函数，以允许你检查值和属性。 一致性测试响应中添加了其中的大多数功能。  
  
> [!NOTE]
>  你需要添加多个验证函数，以使提供程序通过 OLE DB 一致性测试。  
  
 此提供程序需要两个验证例程。 第一个例程， `CRowsetImpl::ValidateCommandID`，是行集类的一部分。 它是由提供程序模板调用的行集创建过程。 此示例使用此例程来告知使用者，它不支持索引。 第一次调用是到`CRowsetImpl::ValidateCommandID`(请注意，提供程序使用 **_RowsetBaseClass** typedef 的接口映射中添加`CMyProviderRowset`中[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)，因此你还没有到类型模板自变量长的行）。 接下来，返回**DB_E_NOINDEX**如果索引参数不是**NULL** （这指示使用者想要在我们使用索引）。 有关命令 Id 的详细信息，请参阅 OLE DB 规范，并查找**IOpenRowset::OpenRowset**。  
  
 下面的代码是**ValidateCommandID**验证例程：  
  
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
  
 提供程序模板调用`OnPropertyChanged`方法每当有人上更改属性**DBPROPSET_ROWSET**组。 如果你想要处理的其他组的属性，你将它们添加到适当的对象 (即， **DBPROPSET_SESSION**检查进入`CMyProviderSession`类)。  
  
 代码首先进行检查，以查看是否属性链接到另一个。 如果正在链接属性，它将设置**DBPROP_BOOKMARKS**属性为 True。 附录 C 的 OLE DB 规范包含有关属性的信息。 此信息还告诉您是否属性链接到另一个。  
  
 你可能还想要添加`IsValidValue`例程到你的代码。 模板调用`IsValidValue`尝试设置属性时。 如果需要额外的处理设置的属性值时，将重写此方法。 你可以为每个属性设置这些方法之一。  
  
## <a name="threading-issues"></a>线程处理问题  
 默认情况下，OLE DB 提供程序中的向导 ATL OLE DB 提供程序向导生成要在单元模型中运行的提供程序的代码。 如果你尝试使用一致性测试运行此代码，一开始就会失败。 这是因为 Ltm.exe，该工具用于运行 OLE DB 一致性测试，默认为自由线程的。 OLE DB 提供程序向导代码将默认为单元模型的性能和易用性。  
  
 若要更正此问题，可以更改 LTM 或更改提供程序。  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>LTM 改为运行在单元线程模式  
  
1.  LTM 主菜单上，单击**工具**，然后单击**选项**。  
  
2.  上**常规**选项卡上，更改从的线程模型**自由线程**到**Apartment Threaded**。  
  
 若要更改你的提供商在可用线程模式下运行：  
  
-   在提供程序项目中，搜索的所有实例`CComSingleThreadModel`并将其替换`CComMultiThreadModel`，这应会在数据源、 会话和行集标头中。  
  
-   在.rgs 文件中，将更改从的线程模型**单元**到**同时**。  
  
-   遵循正确编程编程规则关于自由线程 （即，锁定写入）。  
  
## <a name="see-also"></a>请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)