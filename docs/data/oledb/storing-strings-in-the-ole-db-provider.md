---
title: 将字符串存储在 OLE DB 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84ee07f236ac7ec79149b1cb36f358598f9c6c12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112689"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>将字符串存储在 OLE DB 提供程序中

MyProviderRS.h，ATL OLE DB 提供程序向导创建默认的用户记录调用`CWindowsFile`。 若要处理两个字符串，请修改`CWindowsFile`或添加您自己的用户记录，如下面的代码中所示：  
  
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
  
数据成员`szCommand`并`szText`表示两个字符串，并将`szCommand2`和`szText2`根据需要提供额外的列。 数据成员`dwBookmark`不需要此简单的只读提供程序，但更高版本用于添加`IRowsetLocate`接口; 请参阅[增强简单读取仅提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==`实例进行比较的运算符 （实现此运算符是可选的）。  
  
完成此操作后，您的提供程序应可以随时编译和运行。 若要测试的提供程序，需要具有匹配功能的使用者。 [实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)演示如何创建此类测试使用者。 使用提供程序运行测试使用者。 验证测试使用者从提供程序检索到正确的字符串时，单击**运行**按钮**测试使用者**对话框。  
  
成功测试您的提供程序后，你可能想要通过实现附加接口增强其功能。 一个示例所示[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
## <a name="see-also"></a>请参阅  

[实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)