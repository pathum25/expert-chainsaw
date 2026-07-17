Skip to content

dotnetdotnet-api-docs

Repository navigationCodeIssues1.6k (1.6k)Pull requests100 (100)AgentsActions

This commit does not belong to any branch on this repository, and may belong to a fork outside of the repository.

Commit a902d60

Copilot

authored4 days ago··

Verified

Use xref links and clarify precision caveats in MidpointRounding docs

1 parent 25e511d commit a902d60

1 file changed

+7-7Lines changed: 7 additions & 7 deletions

 

‎xml/System/MidpointRounding.xml‎

Original file line numberOriginal file lineDiff line numberDiff line change

@@ -55,7 +55,7 @@

Use the <xref:System.MidpointRounding> enumeration with appropriate overloads of <xref:System.Math.Round*?displayProperty=nameWithType>, <xref:System.MathF.Round*?displayProperty=nameWithType>, and <xref:System.Decimal.Round*?displayProperty=nameWithType> to provide more control of the rounding process.

Use the <xref:System.MidpointRounding> enumeration with appropriate overloads of <xref:System.Math.Round*?displayProperty=nameWithType>, <xref:System.MathF.Round*?displayProperty=nameWithType>, and <xref:System.Decimal.Round*?displayProperty=nameWithType> to provide more control of the rounding process.

Despite the enumeration's name, not every mode is only about how midpoints are handled. `MidpointRounding` defines two overall rounding strategies&mdash;*round to nearest* and *directed rounding*&mdash;and each enumeration field participates in exactly one of these strategies:

Despite the enumeration's name, not every mode is only about how midpoints are handled. <xref:System.MidpointRounding> defines two overall rounding strategies&mdash;*round to nearest* and *directed rounding*&mdash;and each enumeration field participates in exactly one of these strategies:

- The *round-to-nearest* modes (<xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven>) always round to the nearest representable value. They only differ from each other when the input is exactly halfway between two values (a *midpoint*), which is what the enumeration's name refers to.

- The *round-to-nearest* modes (<xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven>) always round to the nearest representable value. They only differ from each other when the input is exactly halfway between two values (a *midpoint*), which is what the enumeration's name refers to.

- The *directed rounding* modes (<xref:System.MidpointRounding.ToNegativeInfinity>, <xref:System.MidpointRounding.ToPositiveInfinity>, and <xref:System.MidpointRounding.ToZero>) always round every value&mdash;not just midpoints&mdash;in a fixed direction. The result is the nearest representable value in that direction, even when the input isn't a midpoint.

- The *directed rounding* modes (<xref:System.MidpointRounding.ToNegativeInfinity>, <xref:System.MidpointRounding.ToPositiveInfinity>, and <xref:System.MidpointRounding.ToZero>) always round every value&mdash;not just midpoints&mdash;in a fixed direction. The result is the nearest representable value in that direction, even when the input isn't a midpoint.

@@ -69,9 +69,9 @@ Fields:

A round-to-nearest operation takes an original number with an implicit or specified precision; examines the next digit, which is at that precision plus one; and returns the nearest number with the same precision as the original number. For positive numbers, if the next digit is from 0 through 4, the nearest number is toward negative infinity. If the next digit is from 6 through 9, the nearest number is toward positive infinity. For negative numbers, if the next digit is from 0 through 4, the nearest number is toward positive infinity. If the next digit is from 6 through 9, the nearest number is toward negative infinity.

A round-to-nearest operation takes an original number with an implicit or specified precision; examines the next digit, which is at that precision plus one; and returns the nearest number with the same precision as the original number. For positive numbers, if the next digit is from 0 through 4, the nearest number is toward negative infinity. If the next digit is from 6 through 9, the nearest number is toward positive infinity. For negative numbers, if the next digit is from 0 through 4, the nearest number is toward positive infinity. If the next digit is from 6 through 9, the nearest number is toward negative infinity.

If the next digit is from 0 through 4 or 6 through 9, the choice between `MidpointRounding.AwayFromZero` and `MidpointRounding.ToEven` doesn't affect the result of the rounding operation. However, if the next digit is 5, which is the midpoint between two possible results, and all remaining digits are zero or there are no remaining digits, the nearest number is ambiguous. In this case, the round-to-nearest modes in `MidpointRounding` enable you to specify whether the rounding operation returns the nearest number away from zero or the nearest even number.

If the next digit is from 0 through 4 or 6 through 9, the choice between <xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven> doesn't affect the result of the rounding operation. However, if the next digit is 5, which is the midpoint between two possible results, and all remaining digits are zero or there are no remaining digits, the nearest number is ambiguous. In this case, the round-to-nearest modes in <xref:System.MidpointRounding> enable you to specify whether the rounding operation returns the nearest number away from zero or the nearest even number.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with round-to-nearest modes. The precision used to round the numbers is zero, which means the number after the decimal point affects the rounding operation. For example, for the number -2.5, the digit after the decimal point is 5. Because that digit is the midpoint, you can use a `MidpointRounding` value to determine the result of rounding. If `AwayFromZero` is specified, -3 is returned because it is the nearest number away from zero with a precision of zero. If `ToEven` is specified, -2 is returned because it is the nearest even number with a precision of zero.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with round-to-nearest modes. The precision used to round the numbers is zero, which means the number after the decimal point affects the rounding operation. For example, for the number -2.5, the digit after the decimal point is 5. Because that digit is the midpoint, you can use a <xref:System.MidpointRounding> value to determine the result of rounding. If <xref:System.MidpointRounding.AwayFromZero> is specified, -3 is returned because it is the nearest number away from zero with a precision of zero. If <xref:System.MidpointRounding.ToEven> is specified, -2 is returned because it is the nearest even number with a precision of zero.

| Original number | AwayFromZero | ToEven |

| Original number | AwayFromZero | ToEven |

|-----------------|--------------|--------|

|-----------------|--------------|--------|

@@ -92,7 +92,7 @@ Fields:

- <xref:System.MidpointRounding.ToPositiveInfinity>

- <xref:System.MidpointRounding.ToPositiveInfinity>

- <xref:System.MidpointRounding.ToZero>

- <xref:System.MidpointRounding.ToZero>

A directed-rounding operation takes an original number with an implicit or specified precision and returns the next closest number in a specific direction with the same precision as the original number. Directed modes on `MidpointRounding` control the direction toward which every value is rounded. Unlike the round-to-nearest modes, these modes apply to every input value, not just midpoints; for example, `ToPositiveInfinity` rounds 2.1, 2.5, and 2.8 all up to 3.

A directed-rounding operation takes an original number with an implicit or specified precision and returns the next closest number in a specific direction with the same precision as the original number. Directed modes on <xref:System.MidpointRounding> control the direction toward which every value is rounded. Unlike the round-to-nearest modes, these modes apply to every input value, not just midpoints; for example, <xref:System.MidpointRounding.ToPositiveInfinity> rounds 2.1, 2.5, and 2.8 all up to 3.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with directed-rounding modes. The precision used to round the numbers is zero, which means the number before the decimal point is affected by the rounding operation.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with directed-rounding modes. The precision used to round the numbers is zero, which means the number before the decimal point is affected by the rounding operation.

@@ -225,7 +225,7 @@ The following table demonstrates the results of rounding some negative and posit

</ReturnValue>

</ReturnValue>

<MemberValue>3</MemberValue>

<MemberValue>3</MemberValue>

<Docs>

<Docs>

<summary>The strategy of downwards-directed rounding, where every value&mdash;not just midpoints&mdash;is rounded toward negative infinity. The result is the value closest to and no greater than the infinitely precise result. Equivalent to the mathematical floor function.</summary>

<summary>The strategy of downwards-directed rounding, where every value&mdash;not just midpoints&mdash;is rounded toward negative infinity. The result is the value closest to and no greater than the infinitely precise result. When rounding to 

Skip to content

dotnetdotnet-api-docs

Repository navigationCodeIssues1.6k (1.6k)Pull requests100 (100)AgentsActions

This commit does not belong to any branch on this repository, and may belong to a fork outside of the repository.

Commit a902d60

Copilot

authored4 days ago··

Verified

Use xref links and clarify precision caveats in MidpointRounding docs

1 parent 25e511d commit a902d60

1 file changed

+7-7Lines changed: 7 additions & 7 deletions

 

‎xml/System/MidpointRounding.xml‎

Original file line numberOriginal file lineDiff line numberDiff line change

@@ -55,7 +55,7 @@

Use the <xref:System.MidpointRounding> enumeration with appropriate overloads of <xref:System.Math.Round*?displayProperty=nameWithType>, <xref:System.MathF.Round*?displayProperty=nameWithType>, and <xref:System.Decimal.Round*?displayProperty=nameWithType> to provide more control of the rounding process.

Use the <xref:System.MidpointRounding> enumeration with appropriate overloads of <xref:System.Math.Round*?displayProperty=nameWithType>, <xref:System.MathF.Round*?displayProperty=nameWithType>, and <xref:System.Decimal.Round*?displayProperty=nameWithType> to provide more control of the rounding process.

Despite the enumeration's name, not every mode is only about how midpoints are handled. `MidpointRounding` defines two overall rounding strategies&mdash;*round to nearest* and *directed rounding*&mdash;and each enumeration field participates in exactly one of these strategies:

Despite the enumeration's name, not every mode is only about how midpoints are handled. <xref:System.MidpointRounding> defines two overall rounding strategies&mdash;*round to nearest* and *directed rounding*&mdash;and each enumeration field participates in exactly one of these strategies:

- The *round-to-nearest* modes (<xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven>) always round to the nearest representable value. They only differ from each other when the input is exactly halfway between two values (a *midpoint*), which is what the enumeration's name refers to.

- The *round-to-nearest* modes (<xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven>) always round to the nearest representable value. They only differ from each other when the input is exactly halfway between two values (a *midpoint*), which is what the enumeration's name refers to.

- The *directed rounding* modes (<xref:System.MidpointRounding.ToNegativeInfinity>, <xref:System.MidpointRounding.ToPositiveInfinity>, and <xref:System.MidpointRounding.ToZero>) always round every value&mdash;not just midpoints&mdash;in a fixed direction. The result is the nearest representable value in that direction, even when the input isn't a midpoint.

- The *directed rounding* modes (<xref:System.MidpointRounding.ToNegativeInfinity>, <xref:System.MidpointRounding.ToPositiveInfinity>, and <xref:System.MidpointRounding.ToZero>) always round every value&mdash;not just midpoints&mdash;in a fixed direction. The result is the nearest representable value in that direction, even when the input isn't a midpoint.

@@ -69,9 +69,9 @@ Fields:

A round-to-nearest operation takes an original number with an implicit or specified precision; examines the next digit, which is at that precision plus one; and returns the nearest number with the same precision as the original number. For positive numbers, if the next digit is from 0 through 4, the nearest number is toward negative infinity. If the next digit is from 6 through 9, the nearest number is toward positive infinity. For negative numbers, if the next digit is from 0 through 4, the nearest number is toward positive infinity. If the next digit is from 6 through 9, the nearest number is toward negative infinity.

A round-to-nearest operation takes an original number with an implicit or specified precision; examines the next digit, which is at that precision plus one; and returns the nearest number with the same precision as the original number. For positive numbers, if the next digit is from 0 through 4, the nearest number is toward negative infinity. If the next digit is from 6 through 9, the nearest number is toward positive infinity. For negative numbers, if the next digit is from 0 through 4, the nearest number is toward positive infinity. If the next digit is from 6 through 9, the nearest number is toward negative infinity.

If the next digit is from 0 through 4 or 6 through 9, the choice between `MidpointRounding.AwayFromZero` and `MidpointRounding.ToEven` doesn't affect the result of the rounding operation. However, if the next digit is 5, which is the midpoint between two possible results, and all remaining digits are zero or there are no remaining digits, the nearest number is ambiguous. In this case, the round-to-nearest modes in `MidpointRounding` enable you to specify whether the rounding operation returns the nearest number away from zero or the nearest even number.

If the next digit is from 0 through 4 or 6 through 9, the choice between <xref:System.MidpointRounding.AwayFromZero> and <xref:System.MidpointRounding.ToEven> doesn't affect the result of the rounding operation. However, if the next digit is 5, which is the midpoint between two possible results, and all remaining digits are zero or there are no remaining digits, the nearest number is ambiguous. In this case, the round-to-nearest modes in <xref:System.MidpointRounding> enable you to specify whether the rounding operation returns the nearest number away from zero or the nearest even number.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with round-to-nearest modes. The precision used to round the numbers is zero, which means the number after the decimal point affects the rounding operation. For example, for the number -2.5, the digit after the decimal point is 5. Because that digit is the midpoint, you can use a `MidpointRounding` value to determine the result of rounding. If `AwayFromZero` is specified, -3 is returned because it is the nearest number away from zero with a precision of zero. If `ToEven` is specified, -2 is returned because it is the nearest even number with a precision of zero.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with round-to-nearest modes. The precision used to round the numbers is zero, which means the number after the decimal point affects the rounding operation. For example, for the number -2.5, the digit after the decimal point is 5. Because that digit is the midpoint, you can use a <xref:System.MidpointRounding> value to determine the result of rounding. If <xref:System.MidpointRounding.AwayFromZero> is specified, -3 is returned because it is the nearest number away from zero with a precision of zero. If <xref:System.MidpointRounding.ToEven> is specified, -2 is returned because it is the nearest even number with a precision of zero.

| Original number | AwayFromZero | ToEven |

| Original number | AwayFromZero | ToEven |

|-----------------|--------------|--------|

|-----------------|--------------|--------|

@@ -92,7 +92,7 @@ Fields:

- <xref:System.MidpointRounding.ToPositiveInfinity>

- <xref:System.MidpointRounding.ToPositiveInfinity>

- <xref:System.MidpointRounding.ToZero>

- <xref:System.MidpointRounding.ToZero>

A directed-rounding operation takes an original number with an implicit or specified precision and returns the next closest number in a specific direction with the same precision as the original number. Directed modes on `MidpointRounding` control the direction toward which every value is rounded. Unlike the round-to-nearest modes, these modes apply to every input value, not just midpoints; for example, `ToPositiveInfinity` rounds 2.1, 2.5, and 2.8 all up to 3.

A directed-rounding operation takes an original number with an implicit or specified precision and returns the next closest number in a specific direction with the same precision as the original number. Directed modes on <xref:System.MidpointRounding> control the direction toward which every value is rounded. Unlike the round-to-nearest modes, these modes apply to every input value, not just midpoints; for example, <xref:System.MidpointRounding.ToPositiveInfinity> rounds 2.1, 2.5, and 2.8 all up to 3.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with directed-rounding modes. The precision used to round the numbers is zero, which means the number before the decimal point is affected by the rounding operation.

The following table demonstrates the results of rounding some negative and positive numbers in conjunction with directed-rounding modes. The precision used to round the numbers is zero, which means the number before the decimal point is affected by the rounding operation.

@@ -225,7 +225,7 @@ The following table demonstrates the results of rounding some negative and posit

</ReturnValue>

</ReturnValue>

<MemberValue>3</MemberValue>

<MemberValue>3</MemberValue>

<Docs>

<Docs>

<summary>The strategy of downwards-directed rounding, where every value&mdash;not just midpoints&mdash;is rounded toward negative infinity. The result is the value closest to and no greater than the infinitely precise result. Equivalent to the mathematical floor function.</summary>

<summary>The strategy of downwards-directed rounding, where every value&mdash;not just midpoints&mdash;is rounded toward negative infinity. The result is the value closest to and no greater than the infinitely precise result. When rounding to 

