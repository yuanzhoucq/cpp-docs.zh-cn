---
title: 将接口添加到您的提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f50459550c91f07c12f6f18b3fbbaa5622ab7408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032388"
---
# <a name="adding-an-interface-to-your-provider"></a>将接口添加到提供程序

确定你想要将接口添加到 （通常数据源、 行集、 命令或会话对象创建的 OLE DB 提供程序向导） 的对象。 可能需要将添加到接口的对象是一个您的提供程序当前不支持它。 在这种情况下，运行在 ATL OLE DB 提供程序向导来创建对象。 右键单击类视图中的项目，单击**添加类**从**添加**菜单，并单击**ATL OLE DB 访问接口**。 你可能想要将接口代码放在一个单独的目录，然后将文件复制到你提供程序的项目。  
  
如果你创建一个新类来支持接口，请从类中继承的对象。 例如，可能会将类添加**IRowsetIndexImpl**到行集对象：  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
添加到接口**COM_MAP**对象使用 COM_INTERFACE_ENTRY 宏。 如果没有映射，创建一个。 例如：  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
行集对象链的映射其父对象，以便对象可以委托给的父类。 在此示例中，将添加到地图的 COM_INTERFACE_ENTRY_CHAIN 宏：  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)