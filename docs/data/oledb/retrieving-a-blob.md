---
title: "检索 BLOB | Microsoft Docs"
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
  - "BLOB（二进制大对象）, 检索"
  - "OLE DB, BLOB（二进制大对象）"
  - "检索 BLOB"
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 检索 BLOB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以用各种方法检索二进制大对象 \(BLOB\)。  可以使用 **DBTYPE\_BYTES** 将 BLOB 作为一个字节序列来检索，也可以使用一个接口，如 `ISequentialStream`。  有关更多信息，请参见“OLE DB 程序员参考”中的 [BLOBS 和 OLE 对象](https://msdn.microsoft.com/en-us/library/ms711511.aspx)。  
  
 以下代码显示如何使用 `ISequentialStream` 检索 BLOB。  [BLOB\_ENTRY](../../data/oledb/blob-entry.md) 宏使您可以指定该接口以及用于该接口的标志。  打开表后，代码在 `ISequentialStream` 上重复调用 **Read** 以便从 BLOB 中读取字节。  代码调用 **Release** 以便在调用 `MoveNext` 获取下一个记录之前释放接口指针。  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories> > categories;  
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
  
 有关处理 BLOB 数据的宏的更多信息，请参见 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)中的“列映射宏”。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)