---
title: "创建 OLE DB 提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序模板, 创建提供程序"
  - "OLE DB 提供程序, 创建"
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 创建 OLE DB 提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建议以这种方法创建 OLE DB 提供程序：使用向导创建 ATL COM 项目和提供程序，然后使用 OLE DB 模板修改文件。  当自定义提供程序时，可以注释掉不想要的属性和添加可选接口。  
  
 基本步骤如下所示：  
  
1.  使用“ATL 项目向导”创建基本项目文件，并使用“ATL OLE DB 提供程序向导”创建提供程序（在“添加类”中从“Visual C\+\+”文件夹中选择“ATL OLE DB 提供程序”）。  
  
2.  在 CMyProviderRS.h 中修改 `Execute` 方法的代码。  有关示例，请参见[将字符串读入 OLE DB 提供程序](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。  
  
3.  在 MyProviderDS.h、MyProviderSess.h 和 MyProviderRS.h 中编辑属性映射。  向导将创建包含提供程序可能实现的所有属性的属性映射。  仔细检查这些属性映射，移除或注释掉提供程序不需要支持的属性。  
  
4.  更新可以在 MyProviderRS.h 中找到的 PROVIDER\_COLUMN\_MAP。  有关示例，请参见[在 OLE DB 提供程序中存储字符串](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。  
  
5.  当准备好测试提供程序时，可以开始测试，尝试在提供程序枚举中查找它。  有关在枚举中查找提供程序的测试代码示例，请参见 [CATDB](http://msdn.microsoft.com/zh-cn/003d516b-2bf6-444e-8be5-4ebaa0b66046) 和 [DBVIEWER](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832) 示例或[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)中的示例。  
  
6.  添加任何所需的附加接口。  有关示例，请参见[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
    > [!NOTE]
    >  默认情况下，向导生成符合 OLE DB 级别 0 的代码。  为确保应用程序保持符合级别 0，不要从代码中移除向导生成的任何接口。  
  
## 请参阅  
 [CATDB](http://msdn.microsoft.com/zh-cn/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832)