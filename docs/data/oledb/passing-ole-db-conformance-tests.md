---
title: "通过 OLE DB 一致性测试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "一致性测试"
  - "一致性测试 [OLE DB]"
  - "OLE DB 提供程序, 测试"
  - "测试提供程序"
  - "测试, OLE DB 提供程序"
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通过 OLE DB 一致性测试
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了使提供程序更加一致，Data Access SDK 提供了一套 OLE DB 一致性测试。  这些测试检查提供程序的所有方面，并使您可以有理由确信提供程序将按预期的那样运行。  在 Microsoft Data Access SDK 上可以找到 OLE DB 一致性测试。  本节集中讨论应该为通过一致性测试做些什么。  有关运行 OLE DB 一致性测试的信息，请参见 SDK。  
  
## 运行一致性测试  
 在 Visual C\+\+ 6.0 中，OLE DB 提供程序模板添加了若干允许检查值和属性的挂钩函数。  这些函数中的大多数是为响应一致性测试添加的。  
  
> [!NOTE]
>  需要添加若干验证函数以使提供程序通过 OLE DB 一致性测试。  
  
 该提供程序要求两个验证例程。  第一个例程 `CRowsetImpl::ValidateCommandID` 是行集合类的组成部分。  它在行集合的创建期间被提供程序模板调用。  示例使用该例程通知使用者它不支持索引。  第一个调用是对 `CRowsetImpl::ValidateCommandID` 的调用（注意提供程序使用[提供程序的书签支持](../../data/oledb/provider-support-for-bookmarks.md)中在接口映射中为 `CMyProviderRowset` 添加的 **\_RowsetBaseClass** typedef，因此不必键入那一长行模板参数）。  下一步，如果索引参数不为 **NULL**，则返回 **DB\_E\_NOINDEX**（这指示使用者希望使用索引）。  有关命令 ID 的更多信息，请参见 OLE DB 规范并查找 **IOpenRowset::OpenRowset**。  
  
 以下代码是 **ValidateCommandID** 验证例程：  
  
```  
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
  
 每当有人更改 **DBPROPSET\_ROWSET** 组上的属性时，提供程序模板都调用 `OnPropertyChanged` 方法。  如果要处理其他组的属性，则将它们添加到适当的对象（即 **DBPROPSET\_SESSION** 检查在 `CMyProviderSession` 类中进行）。  
  
 代码首先检查属性是否被链接到另一个属性。  如果属性正在被链接，它将 **DBPROP\_BOOKMARKS** 属性设置为 True。  OLE DB 规范的附录 C 包含有关属性的信息。  此信息也告诉您属性是否被链接到另一个属性。  
  
 还可能需要在代码中添加 `IsValidValue` 例程。  模板在尝试设置属性时调用 `IsValidValue`。  如果在设置属性值时需要额外的处理，重写此方法。  对于每个属性集可以拥有这些方法之一。  
  
## 线程问题  
 默认情况下，“ATL OLE DB 提供程序向导”中的“OLE DB 提供程序向导”生成使提供程序在单元模式中运行的代码。  如果尝试对此代码运行一致性测试，一开始就会失败。  这是因为 Ltm.exe 这个用于运行 OLE DB 一致性测试的工具默认为自由线程。  出于性能和易用性方面的考虑，“OLE DB 提供程序向导”代码默认为单元模式。  
  
 若要纠正此问题，可以更改 LTM 或更改提供程序。  
  
#### 将 LTM 改为在单元线程模式中运行  
  
1.  在 LTM 主菜单上，单击“工具”，再单击**“选项”**。  
  
2.  在“常规”选项卡上，将线程模式从“自由线程”更改为“单元线程”。  
  
 将提供程序改为在自由线程模式中运行：  
  
-   在提供程序项目中，搜索 `CComSingleThreadModel` 的所有实例并用 `CComMultiThreadModel` 替换；CComMultiThreadModel 应位于数据源、会话和行集合头中。  
  
-   在 .rgs 文件中，将线程模式从“单元”更改为“两者”。  
  
-   遵循关于自由线程编程的正确编程规则（即锁定写入）。  
  
## 请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)