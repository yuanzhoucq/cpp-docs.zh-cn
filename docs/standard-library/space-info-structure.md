---
title: space_info 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c0e9a636fea95a4ce829731c25605197ee00549
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206730"
---
# <a name="spaceinfo-structure"></a>space_info 结构

保存有关卷的信息。

## <a name="syntax"></a>语法

```cpp
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };
```

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|`unsigned long long available`|表示可用于表示卷上数据的字节数。|
|`unsigned long long capacity`|表示卷可以表示的字节总数。|
|`unsigned long long free`|表示不用于表示卷上数据的字节数。|

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：** std::experimental::filesystem

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[space](https://msdn.microsoft.com/7fce0b0e-523b-4598-b218-47245d0204ca)<br/>
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)<br/>
