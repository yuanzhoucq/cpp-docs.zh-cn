---
title: "创建提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6e590461d359c2ab2ee750f0393f6c2f9ec7ac95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-provider"></a>创建提供程序
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>使用 ATL OLE DB 提供程序向导创建 OLE DB 提供程序  
  
1.  右键单击该项目。  
  
2.  在快捷菜单上，单击**添加**，然后单击**添加类**。  
  
3.  在**添加类**对话框中，选择**ATL OLE DB 访问接口**图标，，然后单击**打开**。  
  
4.  在 ATL OLE DB 提供程序向导中，输入你的提供商中的短名称**短名称**框。 下面的主题使用的短名称"MyProvider"，但你可以使用其他名称。 其他名称框填充根据你输入的名称。  
  
5.  如果需要请编辑的其他名称框。 除了对象和文件名称中，你可以编辑以下：  
  
    -   **组件类**: COM 使用创建提供程序的名称。  
  
    -   **ProgID**： 的编程标识符，是可以使用而不是 GUID 的文本字符串。  
  
    -   **版本**： 的 ProgID 和组件类与用于生成版本依赖型编程 id。  
  
6.  单击 **“完成”**。  
  
## <a name="see-also"></a>请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)