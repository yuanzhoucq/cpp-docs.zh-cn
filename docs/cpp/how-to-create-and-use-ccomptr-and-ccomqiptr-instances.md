---
title: 如何：创建和使用 CComPtr 和 CComQIPtr 实例
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: e376eab75b9b1fb4a7a271d05fe037142f22e139
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246544"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>如何：创建和使用 CComPtr 和 CComQIPtr 实例

在经典 Windows 编程中，库通常作为 COM 对象（更准确地说是 COM 服务器）实现。 很多 Windows 操作系统组件都作为 COM 服务器实现，因此，很多参与者以这种形式提供库。 有关 COM 的基础知识的信息，请参阅 [Component Object Model (COM)](/windows/win32/com/component-object-model--com--portal)。

在实例化组件对象模型 (COM) 对象时，请将接口指针存储在 COM 智能指针中，后者将使用 `AddRef` 和 `Release` 执行引用计数。 如果您使用了活动模板库 (ATL) 或 Microsoft 基础类库 (MFC)，则使用 `CComPtr` 智能指针。 如果没有使用 ATL 或 MFC，则使用 `_com_ptr_t`。 由于没有等效于 `std::unique_ptr`的 COM，请对单个所有者和多个所有者的情况都使用这些智能指针。 `CComPtr` 和 `ComQIPtr` 都支持具有 rvalue 引用的移动操作。

## <a name="example"></a>示例

以下示例演示如何使用 `CComPtr` 实例化 COM 对象并获取指向其接口的指针。 请注意， `CComPtr::CoCreateInstance` 成员函数用于创建 COM 对象，而不是同名的 Win32 函数。

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` 及其亲属是 ATL 的一部分，并且是在 \<atlcomcli.h > 中定义的。 `_com_ptr_t` 在 \<comip.h > 中声明。 当为类型库生成包装器类时，编译器将创建 `_com_ptr_t` 的专用化。

## <a name="example"></a>示例

ATL 还提供了 `CComQIPtr`，它具有用于查询 COM 对象以检索额外接口的更简单的语法。 但是，建议采用 `CComPtr` ，因为它能够执行 `CComQIPtr` 执行的所有操作，并且在语义上与原始 COM 接口指针更一致。 如果您可以使用 `CComPtr` 来查询接口，新接口指针将被放在输出参数中。 如果调用失败，则会返回 HRESULT，它是典型的 COM 模式。 如果使用 `CComQIPtr`，返回值将为指针本身，并且当调用失败时，内部 HRESULT 返回值将无法访问。 以下两行显示了 `CComPtr` 和 `CComQIPtr` 中的错误处理机制的差异。

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>示例

`CComPtr` 提供了针对 IDispatch 的专用化，使它能够存储指向 COM 自动化组件的指针并使用后期绑定调用接口方法。 `CComDispatchDriver` 是 `CComQIPtr<IDispatch, &IIDIDispatch>`（可隐式转换为 `CComPtr<IDispatch>`）的 typedef。 因此，当这三个名称中的任何一个出现在代码中时，它都与 `CComPtr<IDispatch>`等效。 以下示例演示如何使用 `CComPtr<IDispatch>`获取指向 Microsoft Word 对象模型的指针。

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>另请参阅

[智能指针（现代 C++）](../cpp/smart-pointers-modern-cpp.md)
