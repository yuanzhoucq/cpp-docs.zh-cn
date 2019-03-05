---
title: 线程处理模型和关键节类 (ATL)
ms.date: 11/04/2016
f1_keywords:
- vc.atl.threads.models
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
ms.openlocfilehash: 862dd46100f3865b99f965a53b69edc110d6ed80
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257795"
---
# <a name="threading-models-and-critical-sections-classes"></a>线程处理模型和关键节类

以下类定义线程处理模型和关键节：

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md)实现为在线程池的单元模型 COM 服务器。

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md)提供用于实现为在线程池的单元模型 COM 服务器的方法。

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md)提供用于递增和递减变量的线程安全方法。 提供了关键部分。

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md)提供用于递增和递减变量的线程安全方法。 不提供关键部分。

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md)提供用于递增和递减变量的方法。 不提供关键部分。

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel)确定单个对象类的适当线程处理模型类。

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel)确定一个对象，它全局可用的适当线程处理模型类。

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md)包含用于获取并释放关键节的方法。 自动初始化的关键部分。

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md)包含用于获取并释放关键节的方法。 必须显式初始化的关键部分。

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md)镜像中的方法`CComCriticalSection`而无需提供关键部分。 中的方法`CComFakeCriticalSection`不执行任何操作。

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) CRT 线程提供创建函数。 如果该线程将使用的 CRT 函数，请使用此类。

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md)提供了用于 Windows 线程创建函数。 如果该线程不会使用的 CRT 函数，请使用此类。

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)
