---
title: 检索 BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 365b2e5636ecc65ea334730a92953070edd104ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453204"
---
# <a name="retrieving-a-blob"></a>检索 BLOB

您可以检索各种方法中的二进制大型对象 (BLOB)。 可以使用`DBTYPE_BYTES`为一系列字节检索 BLOB 或使用类似的接口`ISequentialStream`。 有关详细信息，请参阅[BLOB 和 OLE 对象](/previous-versions/windows/desktop/ms711511)中**OLE DB 程序员参考**。

下面的代码演示如何检索 BLOB 使用`ISequentialStream`。 该宏[BLOB_ENTRY](../../data/oledb/blob-entry.md)允许您指定的接口和接口使用的标志。 打开后表，该代码调用`Read`重复在`ISequentialStream`从 BLOB 读取字节。 该代码调用`Release`释放之前调用的接口指针`MoveNext`获取下一条记录。

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

然后，使用以下代码：

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

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

有关处理 BLOB 数据的宏的详细信息，请参阅**列映射宏**中[宏和全局函数的 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)<br/>
[OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
