---
title: "检索 BLOB |Microsoft 文档"
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
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e1ded4ce6ae479b555053a1a88290b3e6030c91
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="retrieving-a-blob"></a>检索 BLOB
你可以检索以各种方式二进制大型对象 (BLOB)。 你可以使用**DBTYPE_BYTES**检索为一个字节序列的 BLOB 或使用类似的界面`ISequentialStream`。 有关详细信息，请参阅[BLOB 和 OLE 对象](https://msdn.microsoft.com/en-us/library/ms711511.aspx)中*OLE DB 程序员参考*。  
  
 下面的代码演示如何检索 BLOB 使用`ISequentialStream`。 宏[BLOB_ENTRY](../../data/oledb/blob-entry.md)允许你指定的接口和接口使用的标志。 后打开表，代码调用**读取**重复在`ISequentialStream`从 BLOB 中读取字节。 该代码调用**版本**若要释放之前调用的接口指针`MoveNext`以获取下一条记录。  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
categories.Open(session, "Categories");  

while (categories.MoveNext() == S_OK)  
{  
   do  
   {  
      categories.pPicture->Read(myBuffer, 65536, &cb);  
      // Do something with the buffer  
   } while (cb > 0);  
   categories.pPicture->Release();  
}  
```  
  
 有关处理 BLOB 数据的宏的详细信息，请参阅"列映射宏"中[宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)