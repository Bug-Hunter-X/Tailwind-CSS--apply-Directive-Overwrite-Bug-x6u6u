# Tailwind CSS @apply Directive Overwrite Bug

This repository demonstrates a subtle bug in Tailwind CSS's `@apply` directive. When multiple `@apply` directives modify the same CSS property, only the last one takes effect. This can lead to unexpected visual results that are difficult to debug.

## Bug Description

The bug occurs when using `@apply` to apply multiple utility classes that affect the same CSS property (e.g., `text-color`, `background-color`, etc.).  The order in which these classes are applied determines which style is ultimately applied; the last one overwrites the previous ones. This is unexpected behavior because, logically, one might assume that styles are applied cumulatively or merged in some way.

## Reproduction

1. Clone this repository.
2. Open `bug.html` in your browser.
3. Observe that the text is blue even though both `text-red-500` and `text-blue-500` are applied using `@apply`.

## Solution

The solution is to avoid using multiple `@apply` directives that target the same CSS property if their combined effect is desired.  Instead, create a custom utility class that combines the desired styles or use a single utility class to achieve the intended visual effect. See `solution.html` for a corrected implementation using a custom utility class.

## Additional Notes

This issue highlights the importance of carefully considering the order of `@apply` directives within a class definition. It is crucial to understand that `@apply` is effectively a simple text replacement and does not offer the same level of CSS property merging or specificity handling that a traditional CSS cascade would provide.