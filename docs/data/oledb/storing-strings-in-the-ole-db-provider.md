---
title: "将字符串存储在 OLE DB 提供程序中 | Microsoft Docs"
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
  - "用户记录, 编辑"
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将字符串存储在 OLE DB 提供程序中
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MyProviderRS.h 中，“ATL OLE DB 提供程序向导”创建一条名为 `CWindowsFile` 的默认用户记录。  若要处理两个字符串，请修改 `CWindowsFile`，或者添加自己的用户记录，如以下代码所示：  
  
```  
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 数据成员 `szCommand` 和 `szText` 表示两个字符串，如果需要还包括提供附加列的 `szCommand2` 和 `szText2`。  数据成员 `dwBookmark` 对于此简单的只读提供程序不是必需的，但稍后将用于添加 `IRowsetLocate` 接口；请参见[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  `==` 运算符比较实例（实现此运算符是可选的）。  
  
 完成这些后，提供程序应准备好编译和运行。  若要测试提供程序，需要具有匹配功能的使用者。  [实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)显示如何创建这样的测试使用者。  对提供程序运行测试使用者。  在**“测试使用者”**对话框中单击**“运行”**按钮时，验证测试使用者是否从提供程序中检索到正确的字符串。  
  
 成功地测试了提供程序后，可能需要通过实现附加接口增强其功能。  [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)中显示了一个示例。  
  
## 请参阅  
 [实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)