---
title: _ATL_BASE_MODULE70 结构
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 806ed86076d8b27662bcd9a328d43cabf5df5c86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667540"
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

`cbSize`<br/>
用于版本控制的结构的大小。

`m_hInst`<br/>
`hInstance`此模块 （exe 或 dll）。

`m_hInstResource`<br/>
默认实例的资源句柄。

`m_bNT5orWin98`<br/>
操作系统版本信息。 在内部由 atl。

`dwAtlBuildVer`<br/>
将存储版本的 atl。 当前 0x0700。

`pguidVer`<br/>
ATL 的内部 GUID。

`m_csResource`<br/>
用于同步对`m_rgResourceInstance`数组。 在内部由 atl。

`m_rgResourceInstance`<br/>
用于搜索的 ATL 的识别的所有资源实例中的资源数组。 在内部由 atl。

## <a name="remarks"></a>备注

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定义为 _ATL_BASE_MODULE70 的 typedef。

## <a name="requirements"></a>要求

**标头：** atlcore.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)

