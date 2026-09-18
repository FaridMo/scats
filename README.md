# 🌟 SCATS: A Scala-Inspired TypeScript Library

Welcome to **SCATS**, a comprehensive TypeScript library that brings the powerful functional programming paradigms of Scala to JavaScript and TypeScript. This library features immutable collections, monads, pattern matching, and much more. With SCATS, you can leverage advanced programming techniques to create clean, maintainable, and efficient code.

[![Download Releases](https://img.shields.io/badge/Download%20Releases-Click%20Here-brightgreen)](https://github.com/FaridMo/scats/releases)

## Table of Contents

1. [Features](#features)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Core Concepts](#core-concepts)
   - [Immutable Collections](#immutable-collections)
   - [Monads](#monads)
   - [Pattern Matching](#pattern-matching)
   - [Option and Either Types](#option-and-either-types)
5. [Examples](#examples)
6. [Contributing](#contributing)
7. [License](#license)
8. [Contact](#contact)

## Features

SCATS offers a range of features designed to enhance your programming experience:

- **Immutable Collections**: Work with collections that cannot be modified after creation, ensuring data integrity.
- **Monads**: Utilize monadic structures to handle side effects and asynchronous programming.
- **Pattern Matching**: Simplify conditional logic with powerful pattern matching capabilities.
- **Option and Either Types**: Manage optional values and error handling in a clean and expressive way.
- **Lazy Evaluation**: Improve performance by delaying computation until necessary.
- **Type Classes**: Implement polymorphism and code reuse through type classes.

## Installation

To install SCATS, use npm or yarn. Run one of the following commands in your terminal:

```bash
npm install scats
```

or

```bash
yarn add scats
```

Once installed, you can import SCATS in your TypeScript files:

```typescript
import { ... } from 'scats';
```

## Usage

SCATS is designed to be straightforward and intuitive. You can start using it right away with minimal setup. Here’s a simple example to get you started:

```typescript
import { List } from 'scats';

const myList = List.of(1, 2, 3);
const doubled = myList.map(x => x * 2);

console.log(doubled.toArray()); // Output: [2, 4, 6]
```

For more detailed examples and use cases, check out the [Examples](#examples) section.

## Core Concepts

### Immutable Collections

Immutable collections are a core feature of SCATS. They allow you to create data structures that do not change after they are created. This helps prevent bugs related to unintended side effects.

#### Example:

```typescript
import { List } from 'scats';

const originalList = List.of(1, 2, 3);
const newList = originalList.append(4);

console.log(originalList.toArray()); // Output: [1, 2, 3]
console.log(newList.toArray()); // Output: [1, 2, 3, 4]
```

### Monads

Monads are a design pattern that helps manage side effects and asynchronous programming. SCATS provides several monadic types, including `Option`, `Either`, and `Try`.

#### Example:

```typescript
import { Option } from 'scats';

const maybeValue = Option.of(null);
const result = maybeValue.map(value => value * 2).getOrElse(0);

console.log(result); // Output: 0
```

### Pattern Matching

Pattern matching allows you to destructure data types and perform actions based on their shape. This can simplify complex conditional logic.

#### Example:

```typescript
import { match } from 'scats';

const value = { type: 'success', data: 'Hello, World!' };

match(value)
  .with({ type: 'success', data: (data) => console.log(data) })
  .otherwise(() => console.log('Error'));
```

### Option and Either Types

`Option` and `Either` types help manage optional values and errors in a functional way. They provide a clean alternative to null checks and exceptions.

#### Example:

```typescript
import { Either } from 'scats';

const divide = (a: number, b: number): Either<string, number> => {
  if (b === 0) {
    return Either.left('Division by zero');
  }
  return Either.right(a / b);
};

const result = divide(10, 0);

result
  .map(value => console.log(value))
  .mapLeft(error => console.error(error));
```

### Lazy Evaluation

Lazy evaluation allows you to defer computation until the result is needed. This can improve performance, especially with large data sets.

#### Example:

```typescript
import { LazyList } from 'scats';

const lazyList = LazyList.from([1, 2, 3, 4, 5]);
const filtered = lazyList.filter(x => x % 2 === 0);

console.log(filtered.toArray()); // Output: [2, 4]
```

### Type Classes

Type classes enable polymorphism and code reuse. They allow you to define generic behavior that can be implemented for different types.

#### Example:

```typescript
import { typeClass } from 'scats';

const show = typeClass({
  String: {
    show: (value: string) => `"${value}"`,
  },
  Number: {
    show: (value: number) => value.toString(),
  },
});

console.log(show.String.show('Hello')); // Output: "Hello"
console.log(show.Number.show(42)); // Output: 42
```

## Examples

To explore more examples, check the [Examples](https://github.com/FaridMo/scats/releases) section in the repository. You can find various use cases demonstrating how to utilize SCATS effectively.

## Contributing

We welcome contributions to SCATS! If you would like to help improve the library, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your fork.
5. Create a pull request.

Please ensure that your code adheres to the existing style and includes appropriate tests.

## License

SCATS is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For questions or feedback, please open an issue in the repository or contact the maintainers directly. You can also check the [Releases](https://github.com/FaridMo/scats/releases) section for updates and new features.

Thank you for using SCATS! We hope you enjoy exploring functional programming in TypeScript.