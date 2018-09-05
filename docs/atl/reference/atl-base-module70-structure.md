---
title: _ATL_BASE_MODULE70 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7218d7fc8886cffdcce13f09a682fdc635f84f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759923"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 结构

使用的任何项目都使用 ATL

## <a name="syntax"></a>语法

```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>成员

`cbSize`  
用于版本控制的结构的大小。

`m_hInst`  
`hInstance`此模块 （exe 或 dll）。

`m_hInstResource`  
默认实例的资源句柄。

`m_bNT5orWin98`  
操作系统版本信息。 在内部由 atl。

`dwAtlBuildVer`  
将存储版本的 atl。 当前 0x0700。

`pguidVer`  
ATL 的内部 GUID。

`m_csResource`  
用于同步对`m_rgResourceInstance`数组。 在内部由 atl。

`m_rgResourceInstance`  
用于搜索的 ATL 的识别的所有资源实例中的资源数组。 在内部由 atl。

## <a name="remarks"></a>备注

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定义为 _ATL_BASE_MODULE70 的 typedef。

## <a name="requirements"></a>要求

**标头：** atlcore.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)

