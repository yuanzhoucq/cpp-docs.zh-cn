---
title: 规则中的搜索路径
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: eab6e9d32940aaf5729ce82c4e8258a3a3132208
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825114"
---
# <a name="search-paths-in-rules"></a>规则中的搜索路径

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>备注

推理规则适用于依赖项，仅当完全依赖项中指定的路径与匹配的推理规则路径。 指定在依赖项的目录*frompath*和中的目标目录*topath*; 不允许有空格。 指定只有一条路径的每个扩展。 上一个扩展的路径需要在另一个路径。 若要指定当前目录，请使用句点 （.） 或空大括号 （{}）。 可以表示宏*frompath*并*topath*; 在预处理过程中调用它们。

## <a name="example"></a>示例

### <a name="code"></a>代码

```
{dbi\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUDBI) $<

{ilstore\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{misc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{misc\}.c{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{msf\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{bsc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{mre\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{namesrvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{src\cvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<
```

## <a name="see-also"></a>请参阅

[定义规则](defining-a-rule.md)
