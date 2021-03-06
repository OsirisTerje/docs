---
title: "short (C# Reference)"
ms.date: 03/14/2017
f1_keywords: 
  - "short"
  - "short_CSharpKeyword"
helpviewer_keywords: 
  - "short keyword [C#]"
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
---
# short (C# Reference)

`short` denotes an integral data type that stores values according to the size and range shown in the following table.

|Type|Range|Size|.NET type|
|----------|-----------|----------|-------------------------|
|`short`|-32,768 to 32,767|Signed 16-bit integer|<xref:System.Int16?displayProperty=nameWithType>|

## Literals

You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.  If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.

In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `short` values.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal. Decimal literals have no prefix.

Starting with C# 7.0, a couple of features have been added to enhance readability.

- C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.
- C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix. A decimal literal isn't permitted to have a leading underscore.

Some examples are shown below.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## Compiler overload resolution

A cast must be used when calling overloaded methods. Consider, for example, the following overloaded methods that use `short` and [int](int.md) parameters:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

Using the `short` cast guarantees that the correct type is called, for example:

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## Conversions

There is a predefined implicit conversion from `short` to [int](int.md), [long](long.md), [float](float.md), [double](double.md), or [decimal](decimal.md).

You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](integral-types-table.md) for the storage sizes of integral types). Consider, for example, the following two `short` variables `x` and `y`:

```csharp
short x = 5, y = 12;
```

The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](int.md) by default.

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

To fix this problem, use a cast:

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:

```csharp
int m = x + y;
long n = x + y;
```

There is no implicit conversion from floating-point types to `short`. For example, the following statement generates a compiler error unless an explicit cast is used:

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).

For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## C# language specification

For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md). The language specification is the definitive source for C# syntax and usage.

## See also

- <xref:System.Int16>
- [C# Reference](../index.md)
- [C# Programming Guide](../../programming-guide/index.md)
- [C# Keywords](index.md)
- [Integral Types Table](integral-types-table.md)
- [Built-In Types Table](built-in-types-table.md)
- [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md)
- [Explicit Numeric Conversions Table](explicit-numeric-conversions-table.md)