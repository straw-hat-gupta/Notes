

Focus on Levels 1 to 3 first. Those are most likely to determine your performance, especially in Kelvin’s alarm-data interview.

## Level 1: Core TypeScript

You should be able to write these without much hesitation:

- Primitive types: `string`, `number`, `boolean`
    
- Arrays and objects
    
- Function parameter and return types
    
- `interface` versus `type`
    
- Optional properties: `value?: number`
    
- Nullable values: `number | null`
    
- Union types: `"normal" | "warning" | "critical"`
    
- Type narrowing with `typeof`, `in`, and discriminated unions
    
- `unknown` versus `any`
    
- Arrow functions versus regular functions
    
- Destructuring, spread syntax, and template strings
    
- Truthy and falsy values
    
- `===` versus `==`
    
- Optional chaining: `point?.value`
    
- Nullish coalescing: `value ?? defaultValue`
    

Also understand these common traps:

- `0` is falsy but may be valid sensor data
    
- TypeScript types do not validate runtime input
    
- Objects compare by reference
    
- `sort()` mutates the original array
    
- `NaN` should be checked with `Number.isNaN()`
    

## Level 2: Arrays, parsing, and data transformation

This is the most important level for Kelvin.

### Array methods

Know when and how to use:

- `map`: transform every item
    
- `filter`: keep matching items
    
- `find`: return the first matching item
    
- `some`: check whether at least one item matches
    
- `every`: check whether all items match
    
- `reduce`: aggregate or group items
    
- `forEach`: perform a side effect
    
- `sort`: order items
    
- `slice`: copy or extract part of an array
    

### Data structures

- `Map` for grouping readings by sensor ID
    
- `Set` for duplicate detection
    
- `Record<string, T>` for string-keyed objects
    
- Arrays for ordered data
    
- Choosing between `Map`, `Set`, and plain objects
    

### Parsing and validation

- Parsing JSON
    
- Splitting and trimming strings
    
- Converting strings to numbers
    
- Parsing timestamps with `Date`
    
- Checking invalid timestamps
    
- Validating required fields
    
- Converting raw input into a typed object
    
- Separating parsing from validation
    
- Handling malformed data without crashing
    

### Alarm-data operations

Practise:

- Filtering readings above a threshold
    
- Sorting readings chronologically
    
- Finding the latest reading
    
- Grouping readings by sensor
    
- Counting alarms per sensor
    
- Calculating minimum, maximum, and average values
    
- Removing duplicates
    
- Detecting alarm-state transitions
    
- Detecting consecutive alarm readings
    
- Handling empty and unsorted input
    

## Level 3: Problem-solving and testing

Important for both interviews, particularly Eric’s.

### Problem-solving process

- Clarify input and expected output
    
- Ask about ambiguous requirements
    
- Define types before implementation
    
- Work through a small example
    
- Start with the simplest correct solution
    
- Manually test the result
    
- Explain time and space complexity
    

### Testing concepts

- Unit tests with Jest or Vitest
    
- Arrange, Act, Assert structure
    
- Normal cases and edge cases
    
- Boundary testing, such as `>` versus `>=`
    
- Regression tests
    
- Pure functions
    
- Deterministic tests
    
- Mocking external dependencies
    
- Testing failures and invalid input
    

Always consider:

- Empty arrays
    
- One reading
    
- Duplicate readings
    
- Missing properties
    
- Invalid timestamps
    
- Exact threshold values
    
- Multiple sensors
    
- Unsorted input
    
- Valid zero values
    

### Debugging

- Reproduce the bug first
    
- Isolate the smallest failing case
    
- Read stack traces
    
- Add a failing regression test
    
- Fix the root cause
    
- Run the full test suite
    
- Check for accidental mutation
    
- Watch for missing `await` and unhandled promise rejections
    

## Level 4: Clean design and separation of concerns

This is likely Eric’s main focus.

- Separation of concerns
    
- Single Responsibility Principle
    
- Open/Closed Principle
    
- Dependency Inversion Principle
    
- Dependency injection
    
- Programming against interfaces
    
- Keeping business logic separate from infrastructure
    
- Making functions small and independently testable
    

Be able to split a workflow into:

```text
parseReading
validateReading
evaluateAlarm
saveReading
notifyUser
```

Also review:

- Encapsulation
    
- Abstraction
    
- Polymorphism
    
- Composition versus inheritance
    
- Repository interfaces
    
- Domain objects and business invariants
    
- Controller versus service versus repository responsibilities
    

Know the purpose of these patterns, but you probably will not need to implement all of them:

- Adapter
    
- Facade
    
- Delegate
    
- Factory
    
- Builder
    
- Decorator
    

## Level 5: Async and live-data concepts

Learn these well enough to code a basic example and explain the risks:

- Callbacks
    
- Promises
    
- `async` and `await`
    
- `try/catch`
    
- `Promise.all`
    
- Sequential versus parallel asynchronous work
    
- Node.js event loop
    
- Non-blocking I/O
    
- Event emitters
    

For streaming sensor data:

- WebSockets, Server-Sent Events, and MQTT at a high level
    
- Messages arriving out of order
    
- Duplicate messages
    
- Idempotent processing
    
- Reconnection
    
- Stale connections
    
- Message validation
    
- Backpressure at a conceptual level
    
- Race conditions around shared state
    
- Why PM2 processes cannot safely rely on shared in-memory state
    

## Lower-priority review

Spend limited time on these unless everything above is comfortable:

- React component lifecycle and hooks
    
- Redux Toolkit
    
- Unidirectional data flow
    
- Single source of truth
    
- Immutable state updates
    
- SQL joins, normalization, and indexing
    
- Express controllers and middleware
    
- Azure services
    
- Docker and orchestration
    
- Detailed Domain-Driven Design or Onion Architecture
    

## Best order for the next 4 to 5 days

1. **Day 1:** TypeScript fundamentals and array methods
    
2. **Day 2:** Parsing, validation, grouping, sorting, and alarm problems
    
3. **Day 3:** Testing, debugging, edge cases, and regression prevention
    
4. **Day 4:** Separation of concerns, SOLID, and refactoring exercises
    
5. **Day 5:** Async/live-data concepts and two timed mock interviews
    

Do not spend these days on advanced LeetCode, complex TypeScript generics, or memorizing the entire job description.



---
## First 3 Levels

The fastest approach is one small TypeScript “alarm processor” project, expanded daily. Spend about 20% of your time reading and 80% coding, testing, and explaining aloud.

## Level 1: Learn TypeScript by rewriting simple functions

Spend 2 to 3 hours.

### Learn

Read only the relevant parts of:

- [TypeScript Everyday Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html): arrays, functions, objects, optional properties, unions, interfaces, and type aliases
    
- [TypeScript Narrowing](https://www.typescriptlang.org/docs/handbook/2/narrowing.html): `typeof`, null checks, `in`, and discriminated unions
    

### Practise

Define one data model:

```ts
interface AlarmPoint {
  sensorId: string;
  timestamp: string;
  value: number;
  threshold: number;
  status: "normal" | "warning" | "critical";
}
```

Write these small functions from scratch:

1. Return an alarm’s sensor ID.
    
2. Determine whether its value exceeds its threshold.
    
3. Convert a raw string value into a number.
    
4. Safely handle an optional `value`.
    
5. Accept `string | number` and return a number.
    
6. Format an alarm into a readable message.
    
7. Narrow between valid and invalid alarm results.
    

For every function:

- Explicitly type the parameters.
    
- Explicitly type the return value.
    
- Avoid `any`.
    
- Run the code immediately.
    
- Intentionally pass invalid input and study the compiler error.
    

Do not simply read TypeScript syntax. Type each example yourself, then modify it.

## Level 2: Build an alarm-data exercise ladder

Spend 3 to 4 hours. This should receive the most time.

Create a fixed array containing:

- Several sensors
    
- Normal and critical readings
    
- Duplicate readings
    
- Unsorted timestamps
    
- A zero value
    
- One invalid timestamp
    

Solve these in order:

1. Filter readings above their threshold.
    
2. Transform readings into display messages.
    
3. Find the first critical alarm.
    
4. Check whether any sensor is critical.
    
5. Check whether every reading is valid.
    
6. Sort readings chronologically without changing the input.
    
7. Find the latest reading.
    
8. Group readings by `sensorId`.
    
9. Count critical readings per sensor.
    
10. Remove duplicates using `sensorId + timestamp`.
    
11. Calculate the maximum value per sensor.
    
12. Detect a transition from normal to critical.
    
13. Detect three consecutive critical readings.
    
14. Produce a summary object for every sensor.
    

Use `map`, `filter`, `find`, `some`, `every`, `reduce`, `Map`, and `Set`. MDN’s [array documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) is the best quick reference. Remember that `sort()` changes the original array, while methods such as `map()` and `filter()` return new arrays. [MDN documents that mutation explicitly](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort).

### Best learning loop

For each problem:

1. Solve it with a basic `for...of` loop.
    
2. Solve it again with the appropriate array method or collection.
    
3. Explain why that method fits.
    
4. State the time and space complexity.
    
5. Test empty, single-element, duplicate, and unsorted inputs.
    

Knowing the loop-based solution prevents you from getting stuck if you forget `reduce` syntax.

## Level 3: Add testing and debugging

Spend 2 to 3 hours.

Use [Vitest](https://vitest.dev/guide/) because it supports TypeScript directly and its API is similar to Jest.

For each important function, write tests covering:

- Normal input
    
- Empty array
    
- One reading
    
- Multiple sensors
    
- Duplicate readings
    
- Invalid timestamps
    
- Missing fields
    
- Zero values
    
- Exact threshold
    
- Unsorted input
    
- Input mutation
    

Use this process:

1. Write the expected behaviour.
    
2. Write a failing test.
    
3. Implement the smallest fix.
    
4. Run the test.
    
5. Run the complete test suite.
    
6. Refactor only after everything passes.
    

### Deliberately introduce bugs

Break your own code and diagnose:

- Change `>=` to `>`.
    
- Forget to copy before sorting.
    
- Reject `0` with `if (!value)`.
    
- Compare timestamp strings incorrectly.
    
- Use the wrong grouping key.
    
- Forget to return the accumulator from `reduce`.
    
- Remove an `await`.
    
- Allow a duplicate reading.
    

For each bug, practise saying:

> I would first reproduce the bug with the smallest input, add a regression test, isolate whether the issue is in parsing or the alarm rule, implement the fix, and then run the full suite.

## Recommended schedule

|Day|Focus|
|---|---|
|1|TypeScript fundamentals and six small typed functions|
|2|Alarm exercises 1 through 8|
|3|Alarm exercises 9 through 14, then testing|
|4|One timed five-question Kelvin-style mock|
|5|Debugging practice and another timed mock|

During the timed mocks, do not use autocomplete or documentation for the first attempt. Afterward, use the documentation to correct and rewrite anything that slowed you down.