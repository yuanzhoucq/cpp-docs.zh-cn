---
title: "关于异常的疑难解答：System.NullReferenceException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NullReferenceException 类"
ms.assetid: 4822b0b4-8105-43fb-887a-3cc51ff02899
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.NullReferenceException
当尝试使用值为 <xref:System.NullReferenceException> 的*引用类型*（[C\#](../Topic/Reference%20Types%20\(C%23%20Reference\).md)、[Visual Basic](../Topic/Value%20Types%20and%20Reference%20Types.md)）的方法或属性时，将发生 `null`。 例如，你可能已经尝试在不先使用 [new](../Topic/new%20\(C%23%20Reference\).md) 关键字（Visual Basic 中的 [New](../Topic/New%20Operator%20\(Visual%20Basic\).md)）的情况下使用对象或尝试使用其值被设置为 [null](../Topic/null%20\(C%23%20Reference\).md)（Visual Basic 中的 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)）的对象。  
  
##  <a name="BKMK_Contents"></a> 本文中的章节  
 [本文中使用的类](#BKMK_Classes_used_in_the_examples)  
  
 [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 [在开发期间查找 null 引用异常的源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 [避免 NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 [处理发行代码中的 NullReferenceExceptions](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
##  <a name="BKMK_Classes_used_in_the_examples"></a> 本文中使用的类  
 本文中的大多数示例都使用下面一个或两个类：  
  
```c#  
public class Automobile { public EngineInfo Engine {get; set;} } public class EngineInfo { public EngineInfo() { } public EngineInfo(string powerSrc, double engineSize) { Power = powerSrc; Size = engineSize; } public double Size { get; set; } public string Power = null; }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo End Class Public Class EngineInfo Public Sub New() End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = Nothing End Class  
  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
##  <a name="BKMK_Common_causes_of_NullReferenceExceptions"></a> NullReferenceExceptions 的常见原因  
 任何引用类型变量都可以为 null。 局部变量、类的属性、方法参数以及方法返回值都可以包含 null 引用。 在这些变量为 null 时对它们的方法或属性进行调用会导致 NullReferenceException。 特定情况：  
  
 [已声明但未初始化某个局部变量或成员字段](#BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized)  
  
 [属性或字段为 null](#BKMK_A_property_or_field_is_null)  
  
 [方法参数为 null](#BKMK_A_method_parameter_is_null)  
  
 [方法的返回值为 null](#BKMK_The_return_value_of_a_method_is_null)  
  
 [集合或数组中的某个对象为 null](#BKMK_An_object_in_a_collection_or_array_is_null)  
  
 [由于存在某个条件，所以不创建对象](#BKMK_An_object_is_not_created_because_of_a_condition)  
  
 [通过引用传递给方法的对象设置为 null](#BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null)  
  
###  <a name="BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized"></a> 已声明但未初始化某个局部变量或成员字段  
 这种简单的错误最常发生在 Visual Basic 代码中。 C\# 编译器不允许在未初始化局部引用变量的情况下使用它，但类似于声明要作为输出参数进行传递的变量的情况除外。 Visual Basic 编译器会生成警告。  
  
-   在以下 C\# 代码中，突出显示的行产生此编译器错误：  
  
 **未赋值局部变量“引擎”的使用**  
  
-   在 Visual Basic 代码中，突出显示的行将生成编译器警告 BC42104：  
  
 **变量“引擎”在赋值前被使用。 可能在运行时导致 null 引用异常。**     并且该代码行在运行时会引发 NullReferenceException。  
  
```c#  
public void NullReferencFromUninitializedLocalVariable() { EngineInfo engine; Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferencFromUninitializedLocalVariable() Dim engine As EngineInfo Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_A_property_or_field_is_null"></a> 属性或字段为 null  
 当创建某个类时，该类的字段和属性将自动初始化为其[默认值](../Topic/Data%20Member%20Default%20Values.md)。 引用类的默认值为 `null`（在 Visual Basic 中为 `Nothing`），在字段或属性值为 null 时调用父类的字段或属性的成员方法会导致 NullReferenceException。  
  
 在此示例中，突出显示的代码行将引发 NullReferenceException，因为 `Engine` 的 `car` 属性将自动初始化为 null。  
  
```c#  
public void NullReferenceFromProperty() { var car = new Automobile(); Console.WriteLine(car.Engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferenceFromProperty() Dim car = New Automobile() Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_A_method_parameter_is_null"></a> 方法参数为 null  
 作为引用类型的方法参数可以为 `null`（在 Visual Basic 中为 `Nothing`）。 调用值为 null 的参数的成员方法或属性会导致 NullReferenceException。  
  
 在此示例中，突出显示的代码行将引发 NullReferenceException，由于 `BadEngineInfoPassedToMethod` 使用值为 null 的参数调用 `NullReferenceFromMethodParameter`。  
  
```c  
public void BadEngineInfoPassedToMethod() { EngineInfo eng = null; NullReferenceFromMethodParameter(eng); } public void NullReferenceFromMethodParameter(EngineInfo engine) { Console.WriteLine(engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadParameterPassedToMethod() As EngineInfo Dim eng As EngineInfo = Nothing NullReferenceFromMethodParameter(eng) End Sub Public Sub NullReferenceFromMethodParameter(engine As EngineInfo) Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_The_return_value_of_a_method_is_null"></a> 方法的返回值为 null  
 返回引用类型的方法可返回 `null`（在 Visual Basic 中为 `Nothing`）。 在引用为 null 时，调用返回的引用类型的方法或属性会导致 NullReferenceException。  
  
 在本示例中，突出显示的行将引发 NullReferenceException，因为对 `BadGetEngineInfo` 的调用在 `NullReferenceFromMethodParameter` 方法中返回 null 引用。  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void NullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Function BadGetEngineInfo() As EngineInfo Dim engine As EngineInfo = Nothing Return engine End Function Public Sub NullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() Console.WriteLine(engine.ToString()) End Sub  
  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_in_a_collection_or_array_is_null"></a> 集合或数组中的某个对象为 null  
 引用类型的列表或数组可能包含值为 null 的项。 为 null 的列表项的调用方法或属性会导致 NullReferenceException。  
  
 在此示例中，`NullReferenceFromListItem()` 中突出显示的代码行将引发 NullReferenceException，因为对 `BadGetCarList` 的调用将返回一个值为 null 的项。  
  
```c#  
public Automobile[] BadGetCarList() { var autos = new Automobile[10]; for (int i = 0; i autos.Length; i++) { if (i != 6) { autos[i] = new Automobile(); } } return autos; } public void NullReferenceFromListItem() { var cars = BadGetCarList(); foreach (Automobile car in cars) { Console.WriteLine(car.ToString()); } }  
```  
  
```vb  
Public Function BadGetCarList() As Automobile() Dim autos = New Automobile(10) {} For i As Integer = 0 To 9 If i <> 6 Then autos(i) = New Automobile() End If Next Return autos End Function Public Sub NullReferenceFromListItem() Dim cars = BadGetCarList() For Each car As Automobile In cars Console.WriteLine(car.ToString()) Next End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_is_not_created_because_of_a_condition"></a> 由于存在某个条件，所以不创建对象  
 若在条件块中初始化引用类型，则在该条件为 false 时，将不会创建对象。  
  
 在本示例中，`NullReferenceFromConditionalCreation` 中突出显示的行将引发 NullReferenceException，因为它仅当 `engine` 方法返回 `DetermineTheCondition()` 时才初始化 `true` 变量。  
  
```c#  
public bool DetermineTheCondition() { return false; } public void NullReferenceFromConditionalCreation() { EngineInfo engine = null; var condition = DetermineTheCondition(); if (condition) { engine = new EngineInfo(); engine.Power = "Diesel"; engine.Size = 2.4; } Console.WriteLine(engine.Size); }  
```  
  
```vb  
Public Function DetermineTheCondition() As Boolean Return False End Function Public Sub NullReferenceFromConditionalCreation() Dim engine As EngineInfo = Nothing Dim condition = DetermineTheCondition() If condition Then engine = New EngineInfo() engine.Power = "Diesel" engine.Size = 2.4 End If Console.WriteLine(engine.Size) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
### 传递给方法的对象属性设置为 null  
 当对象作为参数按值传递给方法时（不在 C\# 中使用 `ref` 或 `out` 关键字或在 Visual Basic 中使用 `ByRef`），该方法无法更改参数的内存位置（参数所指向的位置），但可以更改对象的属性。  
  
 在本示例中，`NullPropertyReferenceFromPassToMethod` 方法创建 `Automobile` 对象并初始化 `Engine` 属性。 然后它将调用 `BadSwapCarEngine`，将新对象作为参数传递。`BadSwapCarEngine` 将 Engine 属性设置为 null，这会导致 `NullPropertyReferenceFromPassToMethod` 中突出显示的代码行引发 NullReferenceException。  
  
```c#  
public void BadSwapCarEngine(Automobile car) { car.Engine = null; } public void (Automobile car) { car.Engine = new EngineInfo("GAS", 1.5); BadSwapCarEngine(car); Console.WriteLine(car.Engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadSwapCarEngine(car As Automobile) car.Engine = Nothing End Sub Public Sub NullPropertyReferenceFromPassToMethod() Dim car As New Automobile() car.Engine = New EngineInfo("GAS", 1.5) BadSwapCarEngine(car) Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null"></a> 通过引用传递给方法的对象设置为 null  
 当你通过引用将引用类型作为参数传递给方法（使用 C\# 中的 `ref` 或 `out` 关键字或者 Visual Basic 中的 `ByRef` 关键字）时，你可以更改该参数指向的内存位置。  
  
 如果通过引用将引用类型传递给某个方法，则该方法可以将引用的类型设置为 `null`（在 Visual Basic 中为 `Nothing`）。  
  
 在本示例中，`NullReferenceFromPassToMethodByRef` 中突出显示的行将引发 NullReferenceException，因为对 `BadEngineSwapByRef` 方法的调用将 `stockEngine` 变量设置为 null。  
  
```c#  
public void BadEngineSwapByRef(ref EngineInfo engine) { engine = null; } public void NullReferenceFromPassToMethodByRef() { var stockEngine = new EngineInfo(); stockEngine.Power = "Gas"; stockEngine.Size = 7.0; BadSwapEngineByRef(ref stockEngine); Console.WriteLine(stockEngine.ToString()); }  
```  
  
```vb  
Public Sub BadSwapEngineByRef(ByRef engine As EngineInfo) engine = Nothing End Sub Public Sub NullReferenceFromPassToMethodByRef() Dim formatStr = "The stock engine has been replaced by a {0} liter {} engine" Dim stockEngine = New EngineInfo() stockEngine.Power = "Gas" stockEngine.Size = 7.0 BadSwapEngineByRef(stockEngine) Console.WriteLine(stockEngine.ToString()) End Sub  
  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常见原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_of_a_null_reference_exception_during_development"></a> 在开发期间查找 null 引用异常的源  
 [使用数据提示、“局部变量”窗口和“监视”窗口来查看变量值](#BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values)  
  
 [遍历调用堆栈以查找何处未初始化引用变量或未将其设置为 null](#BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_)  
  
 [将条件断点设置为在对象为 null（在 Visual Basic 中为 Nothing）时停止调试](#BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_)  
  
###  <a name="BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values"></a> 使用数据提示、“局部变量”窗口和“监视”窗口来查看变量值  
  
-   将指针放在变量名上，可以在 [data tip](../Topic/View%20data%20values%20in%20Data%20Tips%20%20in%20the%20code%20editor.md) 中查看它的值。 如果变量引用某个对象或集合，你可以通过展开数据类型检查其属性或元素。  
  
-   打开“局部变量”窗口，检查在当前上下文中处于活动状态的变量。  
  
-   使用[“监视”窗口](../Topic/Watch%20and%20QuickWatch%20Windows.md)关注变量如何在你逐句通过代码代码时发生更改。  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在开发期间查找 null 引用异常的源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_"></a> 遍历调用堆栈以查找何处未初始化引用变量或未将其设置为 null  
 Visual Studio[“调用堆栈”窗口](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)显示了当调试器在异常或断点处停止时尚未完成的方法的名称列表。 你可以在“调用堆栈”窗口中选择名称，然后选择“切换到帧”以更改方法的执行上下文并检查其变量。  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在开发期间查找 null 引用异常的源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_"></a> 将条件断点设置为在对象为 null（在 Visual Basic 中为 Nothing）时停止调试  
 你可以设置当变量为 null 时进行中断的[条件断点](http://msdn.microsoft.com/library/5557y8b4.aspx#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。 条件断点在不经常发生 null 引用时（例如，当集合中的项仅间歇性为 null 时）十分有用。 条件断点的另一个优点是，使你可以在提交到特定处理例程之前调试问题。  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在开发期间查找 null 引用异常的源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
##  <a name="BKMK_Avoid_NullReferenceExceptions"></a> 避免 NullReferenceExceptions  
 [使用 Debug.Assert 来确认固定参数](#BKMK_Use_Debug_Assert_to_confirm_an_invariant)  
  
 [完全初始化引用类型](#BKMK_Fully_initialize_reference_types)  
  
###  <a name="BKMK_Use_Debug_Assert_to_confirm_an_invariant"></a> 使用 Debug.Assert 来确认固定参数  
 *“固定”*指你确信是 true 的条件。[Debug.Assert \(System.Diagnostics\)](http://msdn.microsoft.com/library/system.diagnostics.debug.assert.aspx) 语句只能从调试版的应用中调用，不能从发行代码中调用。 若固定参数条件不为 true，则调试器将在 Assert 语句处中断，并且将显示一个对话框。`Debug.Assert` 将检查在开发应用时条件是否未发生更改。 断言还介绍有关其他人阅读你的代码始终必须满足的条件。  
  
 例如，`MakeEngineFaster` 方法假设它的 `engine` 参数绝不会是 null，因为已知它仅有的调用方法 \(`TheOnlyCallerOfMakeEngineFaster`\) 对 `EngineInfo` 进行完整初始化。`MakeEngineFaster` 中的断言记录了该假设并检查该假设是否为 true。  
  
 如果某人添加不会初始化该参数的新调用方法 \(`BadNewCallerOfMakeEngineFaster`\)，将触发该断言。  
  
```c#  
private void TheOnlyCallerOfMakeEngineFaster() { var engine = new EngineInfo(); engine.Power = "GAS"; engine.Size = 1.5; MakeEngineFaster(engine); } private void MakeEngineFaster(EngineInfo engine) { System.Diagnostics.Debug.Assert(engine != null, "Assert: engine != null"); engine.Size *= 2; Console.WriteLine("The engine is twice as fast"); } private void BadNewCallerOfMakeEngineFaster() { EngineInfo engine = null; MakeEngineFaster(engine); }  
```  
  
```vb  
Public Sub TheOnlyCallerOfMakeEngineFaster() Dim engine As New EngineInfo engine.Power = "GAS" engine.Size = 1.5 MakeEngineFaster(engine) End Sub Private Sub MakeEngineFaster(engine As EngineInfo) System.Diagnostics.Debug.Assert(engine IsNot Nothing, "Assert: engine IsNot Nothing") engine.Size = engine.Size * 2 Console.WriteLine("The engine is twice as fast") End Sub Public Sub BadNewCallerOfMakeEngineFaster() Dim engine As EngineInfo = Nothing MakeEngineFaster(engine) End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [避免 NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_Fully_initialize_reference_types"></a> 完全初始化引用类型  
 为了避免许多 NullReferenceExceptions，请在创建引用类型后尽快将其完全初始化。  
  
 **向你自己的类添加完整初始化**  
  
 若要控制引发 NullReferenceException 的类，则可以考虑在类型的构造函数中完全初始化对象。 例如，以下是用于确保完全初始化的示例类修改后的版本：  
  
```c#  
public class Automobile { public EngineInfo Engine { get; set; } public Automobile(){this.Engine = new EngineInfo();} public Automobile(string powerSrc, double engineSize) { this.Engine = new EngineInfo(powerSrc, engineSize); } } public class EngineInfo { public double Size {get; set;} public string Power {get; set;} public EngineInfo(){// the base enginethis.Power = "GAS";this.Size = 1.5;} public EngineInfo(string powerSrc, double engineSize) { this.Power = powerSrc; this.Size = engineSize; } }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo     Public Sub New()Me.Engine = New EngineInfo()End SubPublic Sub New(powerSrc As String, engineSize As Double)Me.Engine = New EngineInfo(powerSrc, engineSize)End Sub End Class Public Class BaseEngineInfo Public Sub New()' the base engineMe.Power = "GAS"Me.Size = 1.5End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = String.Empty End Class  
```  
  
> [!NOTE]
>  **针对大型属性或不常用的属性使用延迟初始化**  
>   
>  若要减少类的内存占用大小并需要提高其性能，请考虑使用引用类型属性的延迟初始化。 请参阅 [延迟初始化](../Topic/Lazy%20Initialization.md)。  
  
##  <a name="BKMK_Handle_NullReferenceExceptions_in_release_code"></a> 处理发行代码中的 NullReferenceExceptions  
 [在使用引用类型之前检查 null（Visual Basic 中为 Nothing）](#BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type)  
  
 [用 try – catch – finally（在 Visual Basic 中为 Try – Catch – Finally）处理异常](#BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception)  
  
 提前避免 NullReferenceException 比在发生后才进行处理更好。 处理异常会导致代码更难维护和理解，并且有时会引入其他 bug。 NullReferenceException 通常为不可恢复的错误。 在这些情况下，让异常停止应用可能是最佳替代方法。  
  
 然而，在许多情况下，处理错误可能非常有用：  
  
-   你的应用可以忽略为 null 的对象。 例如，如果你的应用检索并处理数据库中的记录，则你可以忽略一些导致 null 对象的错误记录。 你可能仅需在日志文件或应用程序 UI 中记录错误数据。  
  
-   可以从异常中恢复。 例如，在连接丢失或连接超时的情况下，对返回引用类型的 Web 服务的调用可能会返回 null。 可尝试重新建立连接并再次尝试调用。  
  
-   可将你的应用状态还原到有效状态。 例如，你可能要执行多步骤的任务，该任务需要你在调用引发 NullReferenceException 的方法之前将信息保存到数据存储。 如果未初始化的对象可能会损坏数据记录，你可以在关闭应用之前删除之前的数据。  
  
-   你需要报告异常。 例如，如果该错误由应用用户的某个错误引起，你可以生成一条可帮助该用户提供正确信息的消息。 你还可以记录有关该错误的信息来帮助你解决此问题。 某些框架（如 ASP.NET）具有高级别的异常处理程序，该处理程序可捕获所有错误，以便应用永远不会发生崩溃，在这种情况下，记录异常可能是你用来了解是否发生异常的唯一方式。  
  
 下面是处理发行代码中的 NullReferenceException 的两种方式。  
  
###  <a name="BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type"></a> 在使用引用类型之前检查 null（Visual Basic 中为 Nothing）  
 在使用对象之前针对 null 使用显式测试，可避免 try\-catch\-finally 构造对性能的影响。 但是，你仍需要确定并实现在响应未初始化的对象时执行的操作。  
  
 在本示例中，`CheckForNullReferenceFromMethodReturnValue` 测试 `BadGetEngineInfo` 方法的返回值。 若对象不为 null，则可用；否则，该方法将报告错误。  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void CheckForNullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); if(engine != null) { // modify the info engine.Power = "DIESEL"; engine.Size = 2.4; } else { // report the error Console.WriteLine("BadGetEngine returned null") } }  
  
```  
  
```vb  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } Public Sub CheckForNullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() If (engine IsNot Nothing) Then ' modify the info engine.Power = "DIESEL" engine.Size = 2.4 Else ' report the error Console.WriteLine("BadGetEngineInfo returned Nothing") End If End Sub  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [处理发行代码中的 NullReferenceExceptions](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
###  <a name="BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception"></a> 用 try – catch – finally（在 Visual Basic 中为 Try – Catch – Finally）处理异常  
 通过使用内置异常处理构造（在 C\# 中为 [try, catch, finally](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)，在 Visual Basic 中为 [Try, Catch, Finally](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)），除了检查要使用的对象是否不为 null 之外，还可为你提供更多用于处理 NullReferenceExceptions 的选项。  
  
 在此示例中，`CatchNullReferenceFromMethodCall` 会使用两个断言来确认关于它的参数中包含完整 Automobile 对象（包括 Engine 属性）的假设。 在 `try` 块中，突出显示的代码行将引发 NullReferenceException，因为对 `RarelyBadEngineSwap` 的调用将销毁 Car 对象的 `Engine` 属性。`catch` 块捕获异常、将异常信息写入文件并向用户报告错误。 在 `finally` 块中，该方法将确保 Car 的状态并不比方法开始时差。  
  
```c#  
public void RarelyBadSwapCarEngine(Automobile car) { if ((new Random()).Next() == 42) { car.Engine = null; } else { car.Engine = new EngineInfo("DIESEL", 2.4); } } public void CatchNullReferenceFromMethodCall(Automobile car) { System.Diagnostics.Debug.Assert(car != null, "Assert: car != null"); System.Diagnostics.Debug.Assert(car.Engine != null, "Assert: car.Engine != null"); // save current engine properties in case they're needed var enginePowerBefore = car.Engine.Power; var engineSizeBefore = car.Engine.Size; try { RarelyBadSwapCarEngine(car); var msg = "Swap succeeded. New engine power source: {0} size {1}"; Console.WriteLine(msg, car.Engine.Power, car.Engine.Size); } catch(NullReferenceException nullRefEx) { // write exception info to log file LogException(nullRefEx); // notify the user Console.WriteLine("Engine swap failed. Please call your customer rep."); } finally { if(car.Engine == null) { car.Engine = new EngineInfo(enginePowerBefore, engineSizeBefore); } } }  
  
```  
  
```vb  
Public Sub RarelyBadSwapCarEngine(car As Automobile) If (New Random()).Next = 42 Then car.Engine = Nothing Else car.Engine = New EngineInfo("DIESEL", 2.4) End If End Sub Public Sub CatchNullReferenceFromMethodCall(car As Automobile) System.Diagnostics.Debug.Assert(car IsNot Nothing) System.Diagnostics.Debug.Assert(car.Engine IsNot Nothing) ' save current engine properties in case they're needed Dim powerBefore = car.Engine.Power Dim sizeBefore = car.Engine.Size Try RarelyBadSwapCarEngine(car) Dim msg = "Swap succeeded. New engine power source: {0} size {1}" Console.WriteLine(msg, car.Engine.Power, car.Engine.Size) Catch nullRefEx As NullReferenceException ' write exception info to log file LogException(nullRefEx) ' notify user Console.WriteLine("Engine swap failed. Please call your customer rep.") Finally If car.Engine Is Nothing Then car.Engine = New EngineInfo(powerBefore, sizeBefore) End Try End Sub  
  
```  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [处理发行代码中的 NullReferenceExceptions](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)  
  
## 相关文章  
 [异常设计准则（.NET Framework 设计准则）](http://msdn.microsoft.com/library/ms229014)  
  
 [处理和引发异常（.NET Framework 应用程序要点）](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [如何：接收首次异常通知（.NET Framework 开发指南）](http://msdn.microsoft.com/library/Dd997368)  
  
 [如何：处理 PLINQ 查询中的异常（.NET Framework 开发指南）](http://msdn.microsoft.com/library/Dd460712)  
  
 [托管线程中的异常（.NET Framework 开发指南）](http://msdn.microsoft.com/library/ms228965)  
  
 [异常和异常处理（C\# 编程指南）](http://msdn.microsoft.com/library/ms173160)  
  
 [异常处理语句（C\# 参考）](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally 语句 \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [异常处理 \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [C\+\+\/CLI 中的异常](http://msdn.microsoft.com/library/Hh875008)  
  
 [异常处理（任务并行库）](http://msdn.microsoft.com/library/Dd997415)  
  
 [异常处理（调试）](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [演练：处理并发异常（在 Visual Studio 中访问数据）](http://msdn.microsoft.com/library/ms171936)  
  
 [如何：处理因数据绑定而发生的错误和异常（Windows 窗体）](http://msdn.microsoft.com/library/k26k86tb)  
  
 [处理网络应用 \(XAML\) 中的异常 \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![返回页首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文中的章节](#BKMK_Contents)