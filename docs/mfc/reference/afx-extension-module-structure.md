---
title: AFX_EXTENSION_MODULE 结构
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: e1bdc9d744424ab0ad59be3bd7b815b5122bcd10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292830"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 结构

`AFX_EXTENSION_MODULE` MFC 扩展 Dll 的初始化过程中用来保存 MFC 扩展 DLL 模块的状态。

## <a name="syntax"></a>语法

```
struct AFX_EXTENSION_MODULE
{
    BOOL bInitialized;
    HMODULE hModule;
    HMODULE hResource;
    CRuntimeClass* pFirstSharedClass;
    COleObjectFactory* pFirstSharedFactory;
};
```

#### <a name="parameters"></a>参数

*bInitialized*<br/>
如果 DLL 模块已初始化，则为 TRUE `AfxInitExtensionModule`。

*hModule*<br/>
指定 DLL 模块句的柄。

*hResource*<br/>
指定 DLL 的自定义资源模块的句柄。

*pFirstSharedClass*<br/>
指向信息的指针 (`CRuntimeClass`结构) 有关的 DLL 模块的第一个运行时类。 用于提供运行时类列表的开头。

*pFirstSharedFactory*<br/>
指向 DLL 模块的第一个对象工厂的指针 (`COleObjectFactory`对象)。 用于提供类工厂列表的开头。

## <a name="remarks"></a>备注

MFC 扩展 Dll 需要做两件事中的其`DllMain`函数：

- 调用[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)并检查返回值。

- 创建`CDynLinkLibrary`对象将会导出 DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象，或在具有其自己的自定义资源。

`AFX_EXTENSION_MODULE`结构用来保存一份 MFC 扩展 DLL 的模块状态，包括由 MFC 扩展 DLL 初始化之前执行的普通静态对象构造过程中的运行时类对象的副本`DllMain`是输入。 例如：

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

模块信息存储在`AFX_EXTENSION_MODULE`结构可以复制到`CDynLinkLibrary`对象。 例如：

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>要求

**标头：** afx.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)
