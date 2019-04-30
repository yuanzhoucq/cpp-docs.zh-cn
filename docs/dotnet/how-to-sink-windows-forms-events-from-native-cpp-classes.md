---
title: 如何：接收来自本机 Windows 窗体事件C++类
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: d02bcea4efce03c8fb11650d344468236737cfbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387261"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>如何：接收来自本机 Windows 窗体事件C++类

您可以启用本机C++类，以接收回调从托管 Windows 窗体控件或其他使用 MFC 宏映射格式的窗体中引发的事件。 接收器在视图和对话框中的事件是类似于执行操作的控件相同的任务。

若要执行此操作，需要：

- 附加`OnClick`事件处理程序使用在控件[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)。

- 创建委托映射中使用[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)， [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)，并[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)。

此示例将继续在你做的工作[如何：使用 Windows 窗体执行 DDX/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。

现在，会将关联 MFC 控件 (`m_MyControl`) 调用的托管的事件处理程序委托`OnClick`托管<xref:System.Windows.Forms.Control.Click>事件。

### <a name="to-attach-the-onclick-event-handler"></a>若要将附加的 OnClick 事件处理程序：

1. 将以下代码添加到 BOOL CMFC01Dlg::OnInitDialog 的实现：

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. 将以下代码添加到类 CMFC01Dlg 的声明中的公共部分： 公共 CDialog。

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. 最后，添加实现`OnClick`CMFC01Dlg.cpp 到：

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>请参阅

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
