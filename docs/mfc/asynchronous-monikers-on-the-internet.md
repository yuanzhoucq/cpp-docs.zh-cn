---
title: Internet 上的异步名字对象
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: e7a7ea51bca134e965747db8aac7f8a62822c9eb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305024"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Internet 上的异步名字对象

由于应用程序访问网络的速度较慢，因此 Internet 要求采用新方法来设计应用程序。 应用程序应该异步执行网络访问，以避免用户界面出现停滞。 MFC 类[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)下载文件提供了异步支持。

您可以使用异步名字对象扩展 COM 应用程序，以在 Internet 上异步下载和提供大型对象（例如位图和 VRML 对象）的渐进式呈现。 利用异步名字对象，您可以在 Internet 上下载 ActiveX 控件属性或文件，而无不会阻塞用户界面的响应。

## <a name="advantages-of-asynchronous-monikers"></a>异步名字对象的优点

可使用异步名字对象执行以下操作：

- 下载代码和文件，而不会发生阻塞。

- 下载 ActiveX 控件中的属性，而不会发生阻塞。

- 接收下载进度的通知。

- 跟踪进度和就绪状态信息。

- 向用户提供有关进度的状态信息。

- 允许用户可以随时取消下载。

## <a name="mfc-classes-for-asynchronous-monikers"></a>异步名字对象的 MFC 类

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)派生自[CMonikerFile](../mfc/reference/cmonikerfile-class.md)，后者又派生自[COleStreamFile](../mfc/reference/colestreamfile-class.md)。 
  `COleStreamFile` 对象表示数据流；`CMonikerFile` 对象使用 `IMoniker` 获取数据，而 `CAsyncMonikerFile` 对象异步获取数据。

异步名字对象主要用在启用 Internet 的应用程序和 ActiveX 控件中，以在文件传输过程中提供具有响应能力的用户界面。 最好的例子是使用[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>ActiveX 控件中的数据路径的 MFC 类

MFC 类`CDataPathProperty`并[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)实现可异步加载的 ActiveX 控件属性。 可以在同步启动之后加载异步属性。 异步的 ActiveX 控件重复调用一个回调，以在长时间的属性交换过程中指示新数据的可用性。

`CDataPathProperty` 派生自 `CAsyncMonikerFile`。 `CCachedDataPathProperty` 派生自 `CDataPathProperty`。 若要在 ActiveX 控件中实现异步属性，从派生类`CDataPathProperty`或`CCachedDataPathProperty`，并重写[OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable)和你想要接收其他通知。

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>使用异步名字对象下载文件

1. 声明一个类派生自[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。

1. 重写[OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable)以显示数据。

1. 重写其他成员函数，包括[OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress)， [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding)，并[OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding)。

1. 声明此类的实例并使用它来打开 URL。

有关异步下载 ActiveX 控件中的信息，请参阅[Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)。

## <a name="see-also"></a>请参阅

[MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)
