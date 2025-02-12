1.使用类型断言，将 animal 断言成 Fish：

interface Cat { name: string; run(): void; }

interface Fish { name: string; swim(): void; }

function isFish(animal: Cat | Fish) {

if (typeof (animal as Fish).swim === 'function') {

return true; }

return false; }

这样就可以解决访问 animal.swim 时报错的问题了。

需要注意的是，类型断言只能够「欺骗」TypeScript 编译器，无法避免运行时的错误，反而滥用类型断言可能会导致运行时错误：

  
2.

type Name = string;

type NameResolver = () => string;

type NameOrResolver = Name | NameResolver;

function getName(n: NameOrResolver): Name { if (typeof n === 'string') { return n; } else { return n(); } }

上例中，我们使用 type 创建类型别名。

类型别名常用于联合类型。