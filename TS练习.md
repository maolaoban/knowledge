``````typescript
// 不使用 Pick<T, K> ，实现 TS 内置的 Pick<T, K> 的功能。从类型 T 中选出符合 K 的属性，构造一个新的类型。

interface Todo {

 title: string

 description: string

 completed: boolean

}

type MyPick<T, K extends keyof T = keyof T> = {

[P in K]: TP

}

type TodoPreview = MyPick<Todo, 'title' | 'completed'>

const todo: TodoPreview = {

  title: 'Clean room',

  completed: false,

}

// 实现Readonly

interface Todo {

 title: string

 description: string

}

type MyReadonly<T> = {

 readonly [P in keyof T]: T[P]

}

const todo: MyReadonly<Todo> = {

 title: "Hey",

 description: "foobar"

}

todo.title = "Hello" // Error: cannot reassign a readonly property

todo.description = "barFoo" // Error: cannot reassign a readonly property

// 将一个元组类型转换为对象类型，这个对象类型的键/值和元组中的元素对应。

type TupleToObject<T extends readonly string[]> = {

 [P in T[number]]: P 

}

const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

type result = TupleToObject<typeof tuple> // expected { 'tesla': 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}

// 实现一个First<T>泛型，它接受一个数组T并返回它的第一个元素的类型。

type First<T extends any[]> = T extends [] ? never : T[0]

type arr1 = ['a', 'b', 'c']

type arr2 = [3, 2, 1]

type head1 = First<arr1> // 应推导出 'a'

type head2 = First<arr2> // 应推导出 3

// 创建一个Length泛型，这个泛型接受一个只读的元组，返回这个元组的长度。

type Length<T extends readonly any[]> = T['length']

type tesla = ['tesla', 'model 3', 'model X', 'model Y']

type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

type teslaLength = Length<tesla> // expected 4

type spaceXLength = Length<spaceX> // expected 5

// 实现内置的 Exclude<T, U> 类型，从联合类型 T 中排除 U 中的类型，来构造一个新的类型。

type MyExclude<T, K> = T extends K ? never : T

type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'

// 假如我们有一个 Promise 对象，这个 Promise 对象会返回一个类型。

// 在 TS 中，我们用 Promise 中的 T 来描述这个 Promise 返回的类型。

type MyAwaited<T extends Promise<any>> = 

 T extends Promise<infer U> ? U extends Promise<any> ? MyAwaited<U> : U : never;

type ExampleType = Promise<string>

type Result = MyAwaited<ExampleType> // string

// 实现一个 IF 类型，它接收一个条件类型 C ，一个判断为真时的返回类型 T ，以及一个判断为假时的返回类型 F。 

// C 只能是 true 或者 false， T 和 F 可以是任意类型。

type If<C extends Boolean, T, F> = C extends true ? T : F;

type A = If<true, 'a', 'b'>  // expected to be 'a'

type B = If<false, 'a', 'b'> // expected to be 'b'

// 在类型系统里实现 JavaScript 内置的 Array.concat 方法，

// 这个类型接受两个参数，返回的新数组类型应该按照输入参数从左到右的顺序合并为一个新的数组。

type Concat<T extends any[], K extends any[]> = [...T, ...K];

type Result = Concat<[1], [2]> // expected to be [1, 2]

// 在类型系统里实现 JavaScript 的 Array.includes 方法，这个类型接受两个参数，返回的类型要么是 true 要么是 false。

type Includes<T extends readonly any[], K> = any;

type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`

// 在类型系统里实现通用的 Array.push

type Push<T extends any[], K>  = [...T, K];

type Result = Push<[1, 2], '3'> // [1, 2, '3']

// 实现类型版本的 Array.unshift

type Unshift<T extends any[], K> = [K, ...T];

type Result = Unshift<[1, 2], 0> // [0, 1, 2];

// 实现内置的 Parameters 类型

type MyParameters<T> = T extends (...args: infer K) => any ? K : never;

const foo = (arg1: string, arg2: number): void => {}

type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]

// 不使用 ReturnType 实现 TypeScript 的 ReturnType<T> 泛型。

type MyReturnType<T extends (...args: any[]) => unknown> = T extends (...args: any[]) => infer R ? R : never;

const fn = (v: boolean) => {

 if (v)

  return 1

 else

  return 2

}

type a = MyReturnType<typeof fn> // 应推导出 "1 | 2"

// 不使用 Omit 实现 TypeScript 的 Omit<T, K> 泛型。Omit 会创建一个省略 K 中字段的 T 对象。

type MyOmit<T extends object, K extends keyof T> = {

[P in Exclude<keyof T, K>]: TP

}

interface Todo {

 title: string

 description: string

 completed: boolean

}

type TodoPreview = MyOmit<Todo, 'description' | 'title'>

const todo: TodoPreview = {

 completed: false,

}
``````

