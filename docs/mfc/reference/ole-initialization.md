---
title: OLE 初始化
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 6860697dd3adbe26197dd9075e84f402029e00a5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855680"
---
# <a name="ole-initialization"></a>OLE 初始化

必须先初始化 OLE 系统并验证 DLL 是否是正确版本，然后应用程序才能使用 OLE 系统服务。 `AfxOleInit` 函数初始化 OLE 系统 Dll。

### <a name="ole-initialization"></a>OLE 初始化

|||
|-|-|
|[AfxOleInit](#afxoleinit)|初始化 OLE 库。|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。|

## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

在应用程序对象的 `InitInstance` 函数中调用此函数以启用对包含 OLE 控件的支持。

### <a name="syntax"></a>语法

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>备注

有关 OLE 控件（现在称为 ActiveX 控件）的详细信息，请参阅[Activex 控件主题](../mfc-activex-controls.md)。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="afxoleinit"></a>AfxOleInit

初始化应用程序的 OLE 支持。

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>返回值

如果成功，则为非零值;如果初始化失败（可能是因为安装了错误的 OLE 系统 Dll 版本），则为0。

### <a name="remarks"></a>备注

调用此函数可初始化对 MFC 应用程序的 OLE 支持。 调用此函数时，将执行以下操作：

- 初始化调用应用程序当前单元上的 COM 库。 有关详细信息，请参阅[OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize)。

- 创建消息筛选器对象，实现[imessagefilter.prefiltermessage](/windows/win32/api/objidl/nn-objidl-imessagefilter)接口。 可以通过调用[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)访问此消息筛选器。

> [!NOTE]
>  如果从 MFC DLL 调用**AfxOleInit** ，则调用将失败。 发生该错误的原因是，该函数假设从 DLL 中调用 OLE 系统之前已由调用应用程序初始化。

> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元（STA）。 如果在 `InitInstance` 重写中调用[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) ，请指定 COINIT_APARTMENTTHREADED （而不是 COINIT_MULTITHREADED）。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>另请参阅

[宏和全局](../../mfc/reference/mfc-macros-and-globals.md)
