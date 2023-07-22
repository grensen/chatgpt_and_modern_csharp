# Modern C# Programming with ChatGPT

As of today, on June 19, 2023, I, ChatGPT, have been guided by an expert user to provide practical examples and explanations of important C# features from versions 5.0 to 11.0. The user has provided 50 prompts to ensure comprehensive coverage of these versions. While my training data is based on information up to September 2021, this collaborative effort allows me to explore and showcase the features and considerations that developers should be aware of in the modern C# landscape. The user's expertise in C# 11.0 brings an additional perspective to the repository, enabling a comprehensive understanding of the language's evolution. Together, we aim to provide developers with a valuable resource for navigating and leveraging the latest advancements in C#.

## C# 9.0
~~~cs
// 1. Top-level statements
Console.WriteLine("Hello, World!");
// 2. Records
record Person(string FirstName, string LastName);
// 3. Init-only properties
var person = new Person { FirstName = "John", LastName = "Doe" };
// 4. Target-typed new expressions
Person CreatePerson() => new("John", "Doe");
// 5. Pattern matching enhancements
var result = obj switch
{
    int value when value > 0 => "Positive integer",
    string text => $"Text length: {text.Length}",
    _ => "Unknown"
};
// 6. Improved target typing for ternary conditional expressions
object? obj = true;
int number = obj is true ? 1 : 0;
// 7. Lambda discard parameters
Action<int> printNumber = _ => Console.WriteLine("Number: " + _);
printNumber(42);
// 8. Native integers
nint index = 42;
// 9. Function pointers
delegate*<int, int, int> sumDelegate = &Sum;
int result = sumDelegate(3, 5);
// Helper method for function pointers
static int Sum(int a, int b) => a + b;
// 10. Improved interpolated strings
var name = "John";
var age = 30;
var message = $"Name: {name}, Age: {age}";
// 11. Target-typed conditional expressions
object? obj = true;
int number = obj is true ? 1 : 0;
~~~

## C# 8.0
~~~cs
// 1. Nullable reference types
string? nullableString = null;
// 2. Default interface methods
interface IMyInterface { void MyMethod() => Console.WriteLine("Default implementation"); }
// 3. Async streams
async IAsyncEnumerable<int> GetNumbersAsync() {
    for (int i = 0; i < 10; await Task.Delay(100)) yield return i++;
}
// 4. Ranges and indices
int[] numbers = { 1, 2, 3, 4, 5 };
var slice = numbers[1..4];
// 5. Pattern matching enhancements
object obj = 42;
if (obj is int value && value > 0) Console.WriteLine("Positive integer");
// 6. Switch expressions
var dayOfWeek = DateTime.Today.DayOfWeek;
var message = dayOfWeek switch 
{ 
    DayOfWeek.Monday => "It's Monday", 
    DayOfWeek.Friday => "It's Friday", 
    _ => "It's another day" 
};
// 7. Using declarations
using var stream = new FileStream("file.txt", FileMode.Open);
// 8. Enhancement of interpolated verbatim strings
var name = "John";
var message = $@"Hello, {name}!";
// 9. Null-coalescing assignment
int? number = null;
number ??= 42;
// 10. Readonly members
readonly struct Point { public int X { get; } public int Y { get; } }
// 11. Stackalloc in nested expressions
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5 };
~~~

## C# 7.0
~~~cs
// 1. Tuples
var tuple = (1, "hello", true);
// 2. Pattern matching
if (obj is int value) Console.WriteLine($"The value is {value}");
// 3. Out variables
if (int.TryParse("42", out var number)) Console.WriteLine($"Parsed number: {number}");
// 4. Local functions
int Add(int a, int b) => a + b;
// 5. Literal improvements
int binary = 0b1010;
int digitSeparator = 1_000_000;
// 6. Ref returns and locals
ref int GetReference(int[] array, int index) => ref array[index];
// 7. Expression-bodied members
int Multiply(int a, int b) => a * b;
// 8. Throw expressions
void Validate(string value) => _ = value ?? throw new ArgumentNullException(nameof(value));
// 9. Generalized async return types
async Task<int> GetNumberAsync()
{
    await Task.Delay(1000);
    return 42;
}
// 10. Inferred tuple element names
var person = (Name: "John", Age: 30);
// 11. Deconstruction
var (x, y) = GetPoint();
// Helper method for deconstruction
~~~

## C# 6.0
~~~cs
// 1. Auto-implemented properties
public string Name { get; set; } = "John";
// 2. Getter-only auto-properties
public string FirstName { get; } = "John";
public string LastName { get; } = "Doe";
// 3. Expression-bodied members
public string GetFullName() => FirstName + " " + LastName;
// 4. Null-conditional operator
string? text = null;
int? length = text?.Length;
// 5. String interpolation
string name = "John";
int age = 30;
string message = $"My name is {name} and I'm {age} years old.";
// 6. Index initializer for collections
var numbers = new List<int> { 1, 2, 3, 4, 5 };
// 7. nameof expression
string propertyName = nameof(Name);
// 8. Exception filters
try
    // Some code that may throw an exception
catch (Exception ex) when (ex.Message.Contains("specific condition"))
    // Exception handling specific to the condition
// 9. Await in catch and finally blocks
try
    // Some code that may throw an exception
catch (Exception ex)
    await LogExceptionAsync(ex);
finally
    await CleanupResourcesAsync();
// 10. Static using statements
using static System.Math;
double result = Sin(0.5);
// 11. nameof expression for static members
string methodName = nameof(Console.WriteLine);
~~~

## C# 5.0
~~~cs
// 1. Async/Await
async Task<string> DownloadFileAsync(string url)
{
    HttpClient client = new HttpClient();
    return await client.GetStringAsync(url);
}
// 2. Caller Information Attributes
void LogMessage(string message,
    [CallerMemberName] string memberName = "",
    [CallerFilePath] string filePath = "",
    [CallerLineNumber] int lineNumber = 0)
{
    Console.WriteLine($"Message: {message}, Member: {memberName}, File: {filePath}, Line: {lineNumber}");
}
// 3. Improved support for Windows Runtime
using Windows.UI.Xaml.Controls;
namespace MyNamespace
{
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            InitializeComponent();
        }
    }
}
~~~

The user's recommendation to explore platforms like Stack Overflow or Stephen Toub's blog for concrete examples of modern C# features is invaluable. Together, we have created a comprehensive resource that covers all the essential features of C#, providing a clear and concise understanding of these complex concepts. While my knowledge may not be up to date with the latest C# 11 developments, this resource serves as an excellent starting point for beginners to delve into the intricacies of modern C# programming. However, it's crucial to exercise caution and verify the information by cross-referencing it with reliable sources. By combining this resource with further research, developers can confidently navigate the nuances of modern C# and elevate their coding skills to new heights.

## C# 10
~~~cs
// 1. Constant Interpolated Strings
const string Name = "Alan";
const string Designation = $"{Name} - Employee";
// 2. Record Structs
public record struct Point(int X, int Y);
// 3. Improvements of Structure Types
public record struct Person
{
    public string Name { get; init; } = string.Empty;
}
// 4. Custom Interpolated String Handlers
public static class CustomStringHandler
{
    public static string HandleInterpolation(FormattableString formattableString) =>
        $"Custom Handling: {formattableString.Format}";
}
// 5. Global Using Directives
global using System;
global using System.Collections.Generic;
// 6. Implicit Global Usings
<ImplicitUsings>enable</ImplicitUsings>
// 7. Extended Property Patterns
public record Person(string FirstName, string LastName, int Age);
var person = new Person("Shekh", "Ali", 25);
if (person is { FirstName: "Shekh", Age: > 18 })
    Console.WriteLine("This person is over 18 years old");
// 8. Sealed Modifier on ToString in Record Types
public record Person
{
    public string Name { get; init; } = string.Empty;
    public sealed override string ToString() => $"Name: {Name}";
}
// 9. Assignment and Declaration in the Same Deconstruction
var articles = (new Article("Author", "Title"), new CodeMazeArticle("Author", "Title", "Comment"));
var article = new Article("Another author", "Another title");
(article, CodeMazeArticle codeMazeArticle) = articles;
// 10. Lambda Improvements
var lambda = [DebuggerStepThrough] () => "Hello world";
// 11. Null Parameter Checking
void ValidateMail(string email)
{
    ArgumentNullException.ThrowIfNull(email);
    Console.WriteLine($"Email : {email}");
}
// 12. Mutable Property of Record Type
public record Person
{
    public string Name { get; init; } = string.Empty;
}
~~~

## C# 11
~~~cs
// 1. Required Members
public class Person
{
    public required string Name { get; set; }
    public required string Surname { get; set; }
}
// 2. Raw string literals
string name = "Shehryar", surname = "Khan";
string jsonString = $$"""{{""Name"": {{name}},""Surname"": {{surname}}}}""";
// 3. UTF-8 string literals
byte[] array = "Hello World";
// 4. List Patterns
var numbers = new[] { 1, 2, 3, 4 };
Console.WriteLine(numbers is [1, 2, 3, 4]); // True
Console.WriteLine(numbers is [1, 2, 4]); // False
Console.WriteLine(numbers is [_, 2, _, 4]); // True
Console.WriteLine(numbers is [.., 3, _]); // True
Console.WriteLine(numbers is [_, >=2, _, _]); // True
// 5. Newlines in string interpolation expressions
int month = 5;
string season = $"The season is {{month switch {{1 or 2 or 12 => ""winter"",
    > 2 and < 6 => ""spring"", > 5 and < 9 => ""summer""
, > 8 and < 12 => ""autumn"", _ => ""Unknown. Wrong month number""}}}}.";
Console.WriteLine(season); // The season is spring.
// 6. Auto-default structs
public struct Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}
Person person = new() { Name = "John" };
Console.WriteLine(person.Age); // Output: 0
// 7. Pattern match Span<char> on a constant string
if ("SK".AsSpan() is "SK")
    Console.WriteLine("Hey, SK");
// 8. Extended nameof scope
public class MyAttr : Attribute
{
    public MyAttr([CallerArgumentExpression("paramName")] string paramName = "") { }
}
public class MyClass
{
    [MyAttr]
    public void Method(int param, [MyAttr] int anotherParam) { }
}
// 9. An unsigned right-shift operator
int n = -32;
Console.WriteLine($"Before shift: bin = {Convert.ToString(n, 2), 32}, dec = {n}");
int a = n >> 2;
Console.WriteLine($"After >>: bin = {Convert.ToString(a, 2), 32}, dec = {a}");
int b = n >>> 2;
Console.WriteLine($"After >>>: bin = {Convert.ToString(b, 2), 32}, dec = {b}");
~~~


