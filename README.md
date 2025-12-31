# chores-utils

[![npm version](https://img.shields.io/npm/v/chores-utils.svg)](https://www.npmjs.com/package/chores-utils)
[![GitHub](https://img.shields.io/github/license/levidang306/chores-utils)](https://github.com/levidang306/chores-utils/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/levidang306/chores-utils)](https://github.com/levidang306/chores-utils/stargazers)
[![npm downloads](https://img.shields.io/npm/dm/chores-utils.svg)](https://www.npmjs.com/package/chores-utils)

A comprehensive collection of TypeScript utility functions to automate common programming tasks and simplify your development workflow.

<p align="center">
  <a href="https://github.com/levidang306/chores-utils/blob/main/SPONSOR.md">
    <img src="https://img.shields.io/badge/Sponsor-💖-pink.svg" alt="Sponsor">
  </a>
  <a href="https://github.com/levidang306/chores-utils">
    <img src="https://img.shields.io/badge/⭐-Star_on_GitHub-yellow.svg" alt="Star on GitHub">
  </a>
</p>

## Table of Contents

- [Installation](#installation)
- [Features](#features)
- [Usage](#usage)
  - [String Utilities](#string-utilities)
  - [Array Utilities](#array-utilities)
  - [Object Utilities](#object-utilities)
  - [Date Utilities](#date-utilities)
  - [Validation Utilities](#validation-utilities)
  - [Async Utilities](#async-utilities)
  - [Number Utilities](#number-utilities)
- [API Documentation](#api-documentation)
- [Building](#building)
- [Publishing](#publishing)
- [License](#license)
- [Contributing](#contributing)

## Installation

```bash
npm install chores-utils
```

## Features

- 🎯 **Type-safe** - Written in TypeScript with full type definitions
- 📦 **Lightweight** - Zero dependencies
- 🚀 **Modern** - Uses ES2020+ features
- 🔧 **Modular** - Import only what you need
- 📖 **Well-documented** - Clear documentation and examples

## Usage

### String Utilities

```typescript
import { 
  capitalize, 
  toCamelCase, 
  toKebabCase, 
  toSnakeCase,
  truncate,
  isPalindrome 
} from 'chores-utils';

// Capitalize first letter
capitalize('hello world'); // 'Hello world'

// Convert to different cases
toCamelCase('hello world');  // 'helloWorld'
toKebabCase('helloWorld');   // 'hello-world'
toSnakeCase('helloWorld');   // 'hello_world'

// Truncate long strings
truncate('Hello World', 8);  // 'Hello...'

// Check palindrome
isPalindrome('racecar');     // true
```

[View all String functions →](#string-utilities-1)

### Array Utilities

```typescript
import { 
  unique, 
  chunk, 
  flatten, 
  shuffle,
  groupBy,
  intersection,
  difference 
} from 'chores-utils';

// Remove duplicates
unique([1, 2, 2, 3, 3, 4]); // [1, 2, 3, 4]

// Split into chunks
chunk([1, 2, 3, 4, 5], 2);  // [[1, 2], [3, 4], [5]]

// Flatten nested arrays
flatten([[1, 2], [3, 4]]);  // [1, 2, 3, 4]

// Group by property
groupBy(
  [{age: 20}, {age: 30}, {age: 20}], 
  item => item.age
); // { '20': [...], '30': [...] }

// Array operations
intersection([1, 2, 3], [2, 3, 4]); // [2, 3]
difference([1, 2, 3], [2, 3, 4]);   // [1]
```

[View all Array functions →](#array-utilities-1)

### Object Utilities

```typescript
import { 
  deepClone, 
  deepMerge, 
  get, 
  set,
  pick,
  omit 
} from 'chores-utils';

// Deep clone objects
const cloned = deepClone({ a: 1, b: { c: 2 } });

// Deep merge objects
deepMerge(
  { a: 1, b: { c: 2 } }, 
  { b: { d: 3 } }
); // { a: 1, b: { c: 2, d: 3 } }

// Safe nested property access
get({ a: { b: { c: 1 } } }, 'a.b.c');     // 1
get({ a: 1 }, 'a.b.c', 'default');        // 'default'

// Set nested properties
const obj = {};
set(obj, 'a.b.c', 1); // { a: { b: { c: 1 } } }

// Pick/omit properties
pick({ a: 1, b: 2, c: 3 }, ['a', 'c']);   // { a: 1, c: 3 }
omit({ a: 1, b: 2, c: 3 }, ['b']);        // { a: 1, c: 3 }
```

[View all Object functions →](#object-utilities-1)

### Date Utilities

```typescript
import { 
  formatDate, 
  addDays, 
  daysBetween, 
  timeAgo,
  isToday,
  isPast,
  isFuture 
} from 'chores-utils';

// Format dates
formatDate(new Date());           // '2025-12-31'

// Add time periods
addDays(new Date('2025-01-01'), 5);    // 2025-01-06
addMonths(new Date('2025-01-01'), 2);  // 2025-03-01

// Calculate differences
daysBetween(
  new Date('2025-01-01'), 
  new Date('2025-01-10')
); // 9

// Relative time
timeAgo(new Date(Date.now() - 3600000)); // '1 hour ago'

// Date checks
isToday(new Date());              // true
isPast(new Date('2020-01-01'));   // true
isFuture(new Date('2030-01-01')); // true
```

[View all Date functions →](#date-utilities-1)

### Validation Utilities

```typescript
import { 
  isValidEmail, 
  isValidUrl, 
  isValidPhone,
  isStrongPassword,
  isValidHexColor,
  isValidCreditCard 
} from 'chores-utils';

// Validate email
isValidEmail('user@example.com');  // true

// Validate URL
isValidUrl('https://example.com'); // true

// Validate phone
isValidPhone('+1234567890');       // true

// Check password strength
isStrongPassword('P@ssw0rd123');   // true

// Validate hex color
isValidHexColor('#FF5733');        // true

// Validate credit card (Luhn algorithm)
isValidCreditCard('4532015112830366'); // true
```

[View all Validation functions →](#validation-utilities-1)

### Async Utilities

```typescript
import { 
  sleep, 
  retry, 
  debounce, 
  throttle,
  parallelLimit,
  timeout 
} from 'chores-utils';

// Delay execution
await sleep(1000); // Wait 1 second

// Retry with exponential backoff
await retry(
  async () => await fetchData(),
  { retries: 3, delay: 1000, backoff: 2 }
);

// Debounce function calls
const debouncedSearch = debounce(
  (query) => search(query), 
  300
);

// Throttle function calls
const throttledScroll = throttle(
  () => handleScroll(), 
  100
);

// Run tasks with concurrency limit
await parallelLimit(tasks, 3);

// Add timeout to promise
await timeout(fetchData(), 5000);
```

[View all Async functions →](#async-utilities-1)

### Number Utilities

```typescript
import { 
  clamp, 
  round, 
  randomInt,
  sum,
  average,
  percentage,
  formatNumber 
} from 'chores-utils';

// Clamp value between min/max
clamp(10, 0, 5);              // 5

// Round to decimals
round(3.14159, 2);            // 3.14

// Random numbers
randomInt(1, 10);             // Random int between 1-10
randomFloat(0, 1);            // Random float between 0-1

// Array calculations
sum([1, 2, 3, 4]);            // 10
average([1, 2, 3, 4]);        // 2.5

// Percentage
percentage(25, 100);          // 25

// Format with separators
formatNumber(1234567);        // '1,234,567'
```

[View all Number functions →](#number-utilities-1)

## API Documentation

---

### String Utilities (1)

#### `capitalize(str: string): string`
Capitalizes the first letter of a string.

```typescript
capitalize('hello'); // 'Hello'
```

#### `toCamelCase(str: string): string`
Converts a string to camelCase.

```typescript
toCamelCase('hello world'); // 'helloWorld'
toCamelCase('hello-world'); // 'helloWorld'
```

#### `toKebabCase(str: string): string`
Converts a string to kebab-case.

```typescript
toKebabCase('helloWorld'); // 'hello-world'
```

#### `toSnakeCase(str: string): string`
Converts a string to snake_case.

```typescript
toSnakeCase('helloWorld'); // 'hello_world'
```

#### `truncate(str: string, maxLength: number, suffix?: string): string`
Truncates a string to a specified length.

```typescript
truncate('Hello World', 8); // 'Hello...'
truncate('Hello World', 8, '…'); // 'Hello W…'
```

#### `removeWhitespace(str: string): string`
Removes all whitespace from a string.

#### `countOccurrences(str: string, search: string): number`
Counts occurrences of a substring.

#### `reverse(str: string): string`
Reverses a string.

#### `isPalindrome(str: string): boolean`
Checks if a string is a palindrome.

---

### Array Utilities (1)

#### `unique<T>(arr: T[]): T[]`
Removes duplicate values from an array.

```typescript
unique([1, 2, 2, 3, 3, 4]); // [1, 2, 3, 4]
```

#### `chunk<T>(arr: T[], size: number): T[][]`
Chunks an array into smaller arrays of specified size.

```typescript
chunk([1, 2, 3, 4, 5], 2); // [[1, 2], [3, 4], [5]]
```

#### `flatten<T>(arr: any[], depth?: number): T[]`
Flattens a nested array to a specified depth.

```typescript
flatten([[1, 2], [3, 4]]); // [1, 2, 3, 4]
flatten([[[1, 2]], [3, 4]], 2); // [1, 2, 3, 4]
```

#### `shuffle<T>(arr: T[]): T[]`
Shuffles an array randomly.

#### `groupBy<T>(arr: T[], keyFn: (item: T) => string | number): Record<string, T[]>`
Groups array elements by a key function.

```typescript
groupBy([{age: 20}, {age: 30}, {age: 20}], item => item.age);
// { '20': [{age: 20}, {age: 20}], '30': [{age: 30}] }
```

#### `intersection<T>(arr1: T[], arr2: T[]): T[]`
Returns the intersection of two arrays.

```typescript
intersection([1, 2, 3], [2, 3, 4]); // [2, 3]
```

#### `difference<T>(arr1: T[], arr2: T[]): T[]`
Returns the difference between two arrays.

```typescript
difference([1, 2, 3], [2, 3, 4]); // [1]
```

#### `sample<T>(arr: T[]): T | undefined`
Returns a random element from an array.

#### `compact<T>(arr: (T | null | undefined | false | '' | 0)[]): T[]`
Removes falsy values from an array.

#### `range(start: number, end: number, step?: number): number[]`
Creates an array of numbers from start to end.

```typescript
range(1, 5); // [1, 2, 3, 4]
range(0, 10, 2); // [0, 2, 4, 6, 8]
```

---

### Object Utilities (1)

#### `deepClone<T>(obj: T): T`
Deep clones an object.

```typescript
const obj = { a: 1, b: { c: 2 } };
const cloned = deepClone(obj);
```

#### `deepMerge<T>(target: T, source: Partial<T>): T`
Deep merges two objects.

```typescript
deepMerge({ a: 1, b: { c: 2 } }, { b: { d: 3 } });
// { a: 1, b: { c: 2, d: 3 } }
```

#### `get(obj: any, path: string, defaultValue?: any): any`
Gets a nested property value safely.

```typescript
get({ a: { b: { c: 1 } } }, 'a.b.c'); // 1
get({ a: 1 }, 'a.b.c', 'default'); // 'default'
```

#### `set(obj: any, path: string, value: any): void`
Sets a nested property value.

```typescript
const obj = {};
set(obj, 'a.b.c', 1); // { a: { b: { c: 1 } } }
```

#### `omit<T>(obj: T, keys: K[]): Omit<T, K>`
Omits specified keys from an object.

```typescript
omit({ a: 1, b: 2, c: 3 }, ['a', 'c']); // { b: 2 }
```

#### `pick<T>(obj: T, keys: K[]): Pick<T, K>`
Picks specified keys from an object.

```typescript
pick({ a: 1, b: 2, c: 3 }, ['a', 'c']); // { a: 1, c: 3 }
```

#### `invert(obj: Record<string, string>): Record<string, string>`
Inverts keys and values of an object.

#### `isEmptyObject(obj: object): boolean`
Checks if an object is empty.

```typescript
isEmptyObject({});        // true
isEmptyObject({ a: 1 });  // false
```

---

### Date Utilities (1)

#### `formatDate(date: Date): string`
Formats a date to YYYY-MM-DD.

```typescript
formatDate(new Date('2025-12-31')); // '2025-12-31'
```

#### `formatDateTime(date: Date): string`
Formats a date to YYYY-MM-DD HH:mm:ss.

#### `addDays(date: Date, days: number): Date`
Adds days to a date.

```typescript
addDays(new Date('2025-01-01'), 5); // 2025-01-06
```

#### `addMonths(date: Date, months: number): Date`
Adds months to a date.

#### `daysBetween(date1: Date, date2: Date): number`
Gets the difference between two dates in days.

#### `isToday(date: Date): boolean`
Checks if a date is today.

#### `isPast(date: Date): boolean`
Checks if a date is in the past.

#### `isFuture(date: Date): boolean`
Checks if a date is in the future.

#### `timeAgo(date: Date): string`
Gets relative time string.

```typescript
timeAgo(new Date(Date.now() - 3600000)); // '1 hour ago'
```

#### `startOfDay(date: Date): Date`
Gets the start of day for a date.

#### `endOfDay(date: Date): Date`
Gets the end of day for a date.

---

### Validation Utilities (1)

#### `isValidEmail(email: string): boolean`
Validates an email address.

```typescript
isValidEmail('user@example.com'); // true
```

#### `isValidUrl(url: string): boolean`
Validates a URL.

#### `isValidPhone(phone: string): boolean`
Validates a phone number.

#### `isValidCreditCard(cardNumber: string): boolean`
Validates a credit card number using Luhn algorithm.

#### `isStrongPassword(password: string): boolean`
Validates a strong password (8+ chars, upper, lower, number, special char).

#### `isValidHexColor(color: string): boolean`
Validates a hex color code.

```typescript
isValidHexColor('#FF5733'); // true
```

#### `isEmpty(value: any): boolean`
Checks if a value is empty.

#### `isValidIPv4(ip: string): boolean`
Validates an IP address (IPv4).

---

### Async Utilities (1)

#### `sleep(ms: number): Promise<void>`
Delays execution for a specified number of milliseconds.

```typescript
await sleep(1000); // Wait 1 second
```

#### `retry<T>(fn: () => Promise<T>, options?: RetryOptions): Promise<T>`
Retries an async function with exponential backoff.

```typescript
await retry(async () => await fetchData(), {
  retries: 3,
  delay: 1000,
  backoff: 2
});
```

#### `debounce<T>(func: T, wait: number): T`
Debounces a function.

```typescript
const debouncedFn = debounce(() => console.log('Called'), 300);
```

#### `throttle<T>(func: T, limit: number): T`
Throttles a function.

#### `parallelLimit<T>(tasks: (() => Promise<T>)[], limit: number): Promise<T[]>`
Runs promises in parallel with a concurrency limit.

#### `timeout<T>(promise: Promise<T>, ms: number): Promise<T>`
Timeout wrapper for promises.

---

### Number Utilities (1)

#### `clamp(num: number, min: number, max: number): number`
Clamps a number between min and max values.

```typescript
clamp(10, 0, 5); // 5
```

#### `round(num: number, decimals?: number): number`
Rounds a number to specified decimal places.

```typescript
round(3.14159, 2); // 3.14
```

#### `randomInt(min: number, max: number): number`
Generates a random integer between min and max (inclusive).

#### `randomFloat(min: number, max: number): number`
Generates a random float between min and max.

#### `isEven(num: number): boolean` / `isOdd(num: number): boolean`
Checks if a number is even or odd.

#### `sum(numbers: number[]): number`
Calculates the sum of an array of numbers.

#### `average(numbers: number[]): number`
Calculates the average of an array of numbers.

#### `min(numbers: number[]): number` / `max(numbers: number[]): number`
Finds the minimum or maximum value in an array.

#### `toRadians(degrees: number): number` / `toDegrees(radians: number): number`
Converts between degrees and radians.

#### `percentage(value: number, total: number): number`
Calculates percentage.

#### `formatNumber(num: number, locale?: string): string`
Formats a number with thousand separators.

---

## Building

Compile TypeScript files to JavaScript:

```bash
npm run build
```

This will generate the `dist/` directory with compiled JavaScript files and TypeScript declarations.

## Publishing

To publish this package to npm:

1. **Login to npm:**
   ```bash
   npm login
   ```

2. **Update version:**
   ```bash
   npm version patch  # 1.0.0 -> 1.0.1
   npm version minor  # 1.0.0 -> 1.1.0
   npm version major  # 1.0.0 -> 2.0.0
   ```

3. **Publish:**
   ```bash
   npm publish
   ```

## License

MIT © levidang306

## Contributing

Contributions are welcome! Please read our [Contributing Guide](https://github.com/levidang306/chores-utils/blob/main/CONTRIBUTING.md) for details on:

- Reporting bugs
- Suggesting features
- Submitting pull requests
- Code style guidelines

## Support

If you find this package helpful, consider:

- ⭐ [Starring the repository](https://github.com/levidang306/chores-utils)
- 💖 [Sponsoring the project](https://github.com/levidang306/chores-utils/blob/main/SPONSOR.md) - Support via Techcombank
- 🐛 [Reporting issues](https://github.com/levidang306/chores-utils/issues)
- 📖 [Contributing](https://github.com/levidang306/chores-utils/blob/main/CONTRIBUTING.md)

For questions or support, please [open an issue](https://github.com/levidang306/chores-utils/issues).

---

### 💰 Sponsor via Bank Transfer

If this library is useful to you, please consider supporting development:

**Bank**: Techcombank  
**Account**: DANG QUANG NHAT LINH  
**Number**: 3006 2002 36

See [SPONSOR.md](./SPONSOR.md) for QR code and more details.
