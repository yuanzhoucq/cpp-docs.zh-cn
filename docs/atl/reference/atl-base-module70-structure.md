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
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168639"
---
# <a name="_atl_base_module70-structure"></a>_ATL_BASE_MODULE70 结构

由任何使用 ATL 的项目使用。

## <a name="syntax"></a>语法

```cpp
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
此`hInstance`模块（exe 或 dll）的。

`m_hInstResource`<br/>
默认实例资源句柄。

`m_bNT5orWin98`<br/>
操作系统版本信息。 由 ATL 在内部使用。

`dwAtlBuildVer`<br/>
存储 ATL 的版本。 当前0x0700。

`pguidVer`<br/>
ATL 的内部 GUID。

`m_csResource`<br/>
用于同步对数组的`m_rgResourceInstance`访问。 由 ATL 在内部使用。

`m_rgResourceInstance`<br/>
用于在 ATL 可识别的所有资源实例中搜索资源的数组。 由 ATL 在内部使用。

## <a name="remarks"></a>备注

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定义为 _ATL_BASE_MODULE70 的 typedef。

## <a name="requirements"></a>要求

**标头：** atlcore

## <a name="see-also"></a>另请参阅

[类和结构](../../atl/reference/atl-classes.md)
