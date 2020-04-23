---
title: OLE 初始化
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: fefb7eda242ffe15e85cd9f0e16e947a067044a0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751222"
---
# <a name="ole-initialization"></a>OLE 初始化

必须先初始化 OLE 系统并验证 DLL 是否是正确版本，然后应用程序才能使用 OLE 系统服务。 该`AfxOleInit`函数初始化 OLE 系统 DLL。

### <a name="ole-initialization"></a>OLE 初始化

|||
|-|-|
|[AfxOleInit](#afxoleinit)|初始化 OLE 库。|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>Afxenable控制容器

在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。

### <a name="syntax"></a>语法

```cpp
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>备注

有关 OLE 控件（现在称为 ActiveX 控件）的详细信息，请参阅[ActiveX 控件主题](../mfc-activex-controls.md)。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>阿FXOleinit

初始化应用程序的 OLE 支持。

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>返回值

如果成功，则非零;如果初始化失败，则为 0，可能是因为安装了不正确的 OLE 系统 DLL 版本。

### <a name="remarks"></a>备注

调用此函数以初始化 MFC 应用程序的 OLE 支持。 调用此函数时，将执行以下操作：

- 在调用应用程序的当前单元上初始化 COM 库。 有关详细信息，请参阅[Ole 初始化](/windows/win32/api/ole2/nf-ole2-oleinitialize)。

- 创建消息筛选器对象，实现[IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter)接口。 此消息筛选器可通过调用[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)进行访问。

> [!NOTE]
> 如果从 MFC DLL 调用**AfxOleInit，** 则呼叫将失败。 发生失败的原因是，如果函数从 DLL 调用，则以前调用应用程序会初始化 OLE 系统。

> [!NOTE]
> MFC 应用程序必须初始化为单线程单元 （STA）。 如果在`InitInstance`重写中调用[Co初始化Ex，](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)请指定COINIT_APARTMENTTHREADED（而不是COINIT_MULTITHREADED）。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
