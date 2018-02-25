---
title: "将字符串存储在 OLE DB 提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 018bf17cbd4106b4b76ec58ab524d8da6f14b62d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="storing-strings-in-the-ole-db-provider"></a>将字符串存储在 OLE DB 提供程序中
MyProviderRS.h，ATL OLE DB 提供程序向导创建默认用户记录调用`CWindowsFile`。 若要处理这两个字符串，请修改`CWindowsFile`或添加您自己的用户记录，如下面的代码中所示：  
  
```cpp
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
  
 数据成员`szCommand`和`szText`两个字符串，表示与`szCommand2`和`szText2`如果需要提供额外的列。 数据成员`dwBookmark`不需要此简单的只读提供程序，但更高版本用于添加`IRowsetLocate`接口; 请参阅[增强简单读取仅提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==`运算符将实例进行比较 （实现此运算符是可选的）。  
  
 完成此操作后，你的提供商应该已准备好编译和运行。 若要测试提供程序，你需要具有匹配功能的使用者。 [实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)演示如何创建这样的测试使用者。 使用提供程序运行测试使用者。 验证测试使用者从提供程序检索到正确的字符串时您单击**运行**按钮**测试使用者**对话框。  
  
 当你成功地测试你的提供商时，你可能想要通过实现其他接口增强其功能。 一个示例所示[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
## <a name="see-also"></a>请参阅  
 [实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)